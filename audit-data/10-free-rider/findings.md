### [H-1] Marketplace pays the buyer instead of the seller due to post-transfer ownerOf() re-read

**Description:** `FreeRiderNFTMarketplace._buyOne()` transfers the NFT to the buyer 
BEFORE paying the seller, then re-reads `_token.ownerOf(tokenId)` to determine the 
payment recipient. Since the transfer already executed, `ownerOf(tokenId)` now 
returns the BUYER's address — meaning the buyer receives their own payment back 
instead of paying the seller.

Additionally, `buyMany()` checks `msg.value < priceToPay` against the full 
transaction's `msg.value` on every iteration without ever decrementing it — 
allowing a single `msg.value` equal to one NFT's price to satisfy the check 
for all NFTs purchased in the same call.

**Impact:** An attacker can purchase all NFTs in the marketplace for the price 
of one, while the seller receives nothing and the buyer recovers their ETH 
each time. Combined with a Uniswap V2 flash swap to source the initial capital, 
an attacker with near-zero starting funds can acquire the marketplace's entire 
NFT inventory and drain a portion of its ETH balance.

**Proof of Concept:**
1. Flash-swap 15 WETH from the Uniswap V2 pair (token0/WETH), unwrapping to ETH.
2. Call `buyMany()` for all 6 NFTs with `msg.value: 15 ether` — the check passes 
   for every NFT since `msg.value` never decreases; each purchase refunds the 
   price to the buyer due to the ownership bug.
3. Repay the flash swap plus the 0.3% fee from the recovered ETH.
4. Transfer all 6 NFTs to the recovery manager using the 4-argument 
   `safeTransferFrom` with `abi.encode(player)` as data, triggering the bounty 
   payout on the final transfer.

<details>
<summary>Example Code Snippet</summary>

```solidity
function uniswapV2Call(address sender, uint amount0, uint amount1, bytes calldata data) external {
    address payable wethAddr = payable(IUniswapV2Pair(pair).token0());
    WETH(wethAddr).withdraw(amount0);

    uint256[] memory tokenIds = new uint256[](6);
    for (uint256 i = 0; i < 6; i++) { tokenIds[i] = i; }

    marketplace.buyMany{value: 15 ether}(tokenIds);

    uint256 amountToRepay = (amount0 * 1000) / 997 + 1;
    weth.deposit{value: amountToRepay}();
    weth.transfer(address(pair), amountToRepay);
}
             
// After flash swap completes:
bytes memory recipientData = abi.encode(player);
for (uint256 i = 0; i < 6; i++) {
    nft.safeTransferFrom(address(this), recoveryManager, i, recipientData);
}
```
</details>

**Recommended Mitigation:**
1. Cache the seller's address BEFORE transferring the NFT — never re-read 
   `ownerOf()` after the transfer to determine payment recipient.
2. Follow checks-effects-interactions strictly: pay the seller first (or cache 
   the address), then transfer the NFT, not the reverse.
3. In `buyMany()`, deduct each NFT's price from a running total and validate 
   the cumulative sum against `msg.value`, rather than checking the same 
   `msg.value` repeatedly.

<details>
<summary>Mitigation Code</summary>

```solidity
// Cache seller BEFORE the transfer changes ownership — this is the fix.
// Previously ownerOf(tokenId) was read again AFTER the transfer below,
// which returned the buyer's own address instead of the seller's.
address seller = _token.ownerOf(tokenId);
_token.safeTransferFrom(seller, msg.sender, tokenId);
payable(seller).sendValue(priceToPay);
```

```solidity
// Track spend explicitly across the batch instead of re-checking the
// same msg.value on every iteration.
uint256 remainingValue = msg.value;
for (uint256 i = 0; i < tokenIds.length; ++i) {
    remainingValue = _buyOne(tokenIds[i], remainingValue);
}
```
</details>