### High Severity: L1 Gateway Allows Forged Withdrawals by Trusting Unauthenticated Forwarded Messages

**Severity:** High

**Description**

The `L1Gateway::finalizeWithdrawal()` function allows an operator to finalize a withdrawal by supplying arbitrary withdrawal parameters (`nonce`, `l2Sender`, `target`, `timestamp`, and `message`) along with a valid Merkle proof.

The vulnerability is that the gateway does not sufficiently bind the authenticated withdrawal leaf to the semantics of the forwarded call. As a result, an attacker with permission to finalize withdrawals can submit a crafted message that successfully passes verification while executing arbitrary logic through the trusted `L1Forwarder`.

In particular, an attacker can encode a call to:

```solidity
L1Forwarder.forwardMessage(...)
```

which itself forwards an arbitrary call to the L1 token bridge:

```solidity
TokenBridge.executeTokenWithdrawal(player, 990_000e18)
```

Since the gateway ultimately treats the forwarded message as trusted, the bridge executes the withdrawal even though it was never part of the legitimate withdrawal set produced on L2.

This breaks the core security assumption of the bridge: **only authenticated L2 withdrawals should be executable on L1.**

**Impact**

An attacker capable of finalizing withdrawals can execute arbitrary bridge withdrawals that were never initiated on L2.

Depending on the bridge's available liquidity, this allows unauthorized withdrawal of user funds from the L1 bridge.

In the challenge, the attacker is able to withdraw **990,000 DVT** from the bridge without a corresponding legitimate L2 withdrawal.


**Proof of Concept**

The attacker crafts a malicious forwarded message:

```solidity
bytes memory message = abi.encodeCall(
    L1Forwarder.forwardMessage,
    (
        0,
        address(0),
        address(l1TokenBridge),
        abi.encodeCall(
            TokenBridge.executeTokenWithdrawal,
            (player, 990_000e18)
        )
    )
);
```

and finalizes it through the gateway:

```solidity
l1Gateway.finalizeWithdrawal(
    0,
    l2Handler,
    address(l1Forwarder),
    block.timestamp - 7 days,
    message,
    new bytes32[](0)
);
```

The gateway accepts the withdrawal, after which the forwarder executes:

```text
L1Forwarder
    ↓
forwardMessage(...)
    ↓
TokenBridge.executeTokenWithdrawal(...)
```

resulting in an unauthorized transfer of bridge funds to the attacker.

---

**Recommendation**

The gateway should cryptographically authenticate the **entire withdrawal payload** and ensure that the executed message exactly matches the message committed on L2.

In particular:

* Include every executable field (`target`, `l2Sender`, `nonce`, `timestamp`, and `message`) in the authenticated withdrawal leaf.
* Ensure the message executed by `L1Forwarder` is identical to the message committed on L2.
* Prevent arbitrary forwarding to privileged bridge functions unless the forwarded payload is itself authenticated.
* Treat forwarded messages as untrusted until their contents have been fully validated against the authenticated withdrawal commitment.

By binding the executed calldata to the authenticated L2 withdrawal record, forged withdrawal messages cannot be introduced during finalization.
