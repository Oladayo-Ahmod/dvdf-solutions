### [H-1] Rounding-to-zero in shard purchase accounting allows repeated refunds and drains marketplace funds

**Description:** `ShardsNFTMarketplace.fill()` calculates the buyer's payment using
`FixedPointMathLib.mulDivDown()`. For sufficiently small shard purchases, the
payment rounds down to zero while the purchase is still recorded in
`offer.purchases`. Later, `cancel()` refunds based on the stored purchase amount
without distinguishing between free (zero-payment) purchases and paid purchases,
allowing an attacker to repeatedly create refundable positions at no cost.

**Impact:** An attacker can purchase a tiny amount of shards for zero tokens due
to integer rounding, then later acquire the remaining shards normally and cancel
both purchases independently. The second cancellation refunds the full payment,
while the first cancellation returns free shards to the offer, enabling the
attacker to recover the full purchase price yet retain ownership of the entire
NFT. The marketplace permanently loses the refunded tokens.

**Proof of Concept:**

1. Call `fill(offerId, 100)`:

   * Payment is computed with `mulDivDown()` and rounds to **0 DVT**.
   * Purchase is nevertheless recorded in `offer.purchases`.
2. Immediately call `cancel(offerId, 0)`:

   * Free shards are returned to the offer.
   * Purchase entry is deleted.
3. Call `fill(offerId, 1e9)`:

   * Purchase all available shards for the correct payment.
   * Marketplace now holds the payment.
4. Call `cancel(offerId, 1)`:

   * Marketplace refunds the full payment for the second purchase.
   * Attacker keeps the NFT while recovering all spent tokens.
5. Transfer recovered funds to the recovery address.

<details>
<summary>Example Code Snippet</summary>

```solidity
token.approve(address(marketplace), type(uint256).max);

// Purchase rounds down to zero
marketplace.fill(offerId, 100);

// Return free shards
marketplace.cancel(offerId, 0);

// Purchase remaining shards
marketplace.fill(offerId, 1e9);

// Recover full payment
marketplace.cancel(offerId, 1);
```

</details>

**Root Cause:**

The payment is calculated as:

```solidity
payment = wanted.mulDivDown(priceInDVT, totalShards);
```

When:

```text
wanted * priceInDVT < totalShards
```

`mulDivDown()` returns `0`, yet the purchase is still accepted and recorded.
The protocol therefore treats a zero-cost purchase as economically equivalent
to a paid purchase.

**Recommended Mitigation:**

1. Reject purchases whose computed payment is zero.

2. Alternatively, round payments up using `mulDivUp()` so that every successful
   purchase pays at least one unit of the payment token.

3. Enforce a minimum shard purchase size that guarantees a non-zero payment.

<details>
<summary>Mitigation Code</summary>

```solidity
uint256 payment = wanted.mulDivDown(priceInDVT, offer.totalShards);

require(payment > 0, "Purchase too small");
```

or

```solidity
uint256 payment = wanted.mulDivUp(priceInDVT, offer.totalShards);
```

</details>

This prevents economically free purchases from being inserted into the protocol's accounting while preserving correct refund behavior.
