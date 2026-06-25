### [H-1] Lending pool uses manipulable Uniswap V1 spot price as sole collateral oracle

**Description:** `PuppetPool._computeOraclePrice()` derives the token price 
directly from the live ETH/token balance ratio of a single Uniswap V1 exchange — 
`uniswapPair.balance / token.balanceOf(uniswapPair)`. This spot price has no 
manipulation resistance (no TWAP, no external price feed). Any party with 
sufficient capital can swap tokens into the Uniswap pair to crash this ratio, 
since `calculateDepositRequired()` directly scales with this manipulable price.

**Impact:** An attacker can crash the token's oracle price to near-zero by 
swapping their token balance for ETH on Uniswap, then borrow the lending 
pool's entire token reserve for negligible ETH collateral — fully draining 
the pool's tokens.

**Proof of Concept:**
1. Pull player's token balance into an attacker contract.
2. Swap the entire token balance for ETH via `tokenToEthSwapInput()` on the 
   Uniswap V1 exchange — this floods the pair with tokens and drains its ETH, 
   crashing the price.
3. Call `calculateDepositRequired()` — now returns a negligible value due to 
   the crashed price.
4. Call `borrow()` with the pool's full token balance, paying minimal ETH 
   collateral.
5. Transfer all borrowed tokens to the recovery account.

<details>
<summary>Example Code Snippet</summary>

```solidity
function attack(address player, address recovery) external {
    token.transferFrom(player, address(this), PLAYER_INITIAL_TOKEN_BALANCE);
    token.approve(address(uniswapV1Exchange), PLAYER_INITIAL_TOKEN_BALANCE);
    uniswapV1Exchange.tokenToEthSwapInput(PLAYER_INITIAL_TOKEN_BALANCE, 1, block.timestamp);

    lendingPool.borrow{value: PLAYER_INITIAL_ETH_BALANCE}(POOL_INITIAL_TOKEN_BALANCE, address(this));
    token.transfer(recovery, token.balanceOf(address(this)));
}
```
</details>

**Recommended Mitigation:**
1. Never use a single DEX's spot price as a lending collateral oracle — use a 
   time-weighted average price (TWAP) over multiple blocks to resist single-
   transaction manipulation.
2. Use a decentralized oracle network (e.g. Chainlink) for collateral pricing 
   instead of deriving it from on-chain liquidity ratios.
3. Add liquidity depth checks — reject price readings from pools with 
   insufficient liquidity relative to the borrow amount, since thin pools are 
   trivially manipulable.