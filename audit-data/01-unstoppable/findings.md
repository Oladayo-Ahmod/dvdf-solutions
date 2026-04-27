### [H-1] Broken Invariant/ Direct token transfer halting all flash loans

**Description:** In the UnstoppableVault contract, The `flashLoan()` function checks that `convertToShares(totalSupply) 
== totalAssets()`. This assumes token balance only changes via 
`deposit()` and `withdraw()`. A direct ERC20 transfer bypasses 
this accounting, permanently breaking the equality check and 
halting all flash loans.

**Impact:** An attacker can permanently disable flash loans by sending tokens directly to the vault, causing the invariant check to fail and preventing any future flash loan operations. This could disrupt users relying on flash loans for various DeFi strategies.

**Proof of Concept:**
1. Deploy the UnstoppableVault contract and fund it with tokens.
2. An attacker sends tokens directly to the vault's address using a standard ERC20 transfer.
3. After the transfer, any attempt to call `flashLoan()` will fail due to the
invariant check, effectively halting all flash loan functionality.

<>

**Recommended Mitigation:**