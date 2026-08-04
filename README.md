# 0xSpectreSec — Damn Vulnerable DeFi v4 Solutions

> Complete solutions to all 18 DVDF v4 challenges with full audit reports, Foundry PoCs, and vulnerability writeups.

[![X](https://img.shields.io/badge/X-@0xSpectreSec-black?style=flat-square&logo=x)](https://twitter.com/0xSpectreSec)
[![GitHub](https://img.shields.io/badge/GitHub-Oladayo--Ahmod-181717?style=flat-square&logo=github)](https://github.com/Oladayo-Ahmod)

---

## Challenge completion

| # | Challenge | Vulnerability class | Writeup |
|---|-----------|-------------------|---------|
| 01 | Unstoppable | Broken ERC4626 invariant — direct token transfer halts flash loans | [→](./audit-data/01-unstoppable/) |
| 02 | Naive Receiver | ERC-2771 forwarder msgSender spoofing via multicall | [→](./audit-data/02-naive-receiver/) |
| 03 | Truster | Arbitrary calldata execution via flash loan callback | [→](./audit-data/03-truster/) |
| 04 | Side Entrance | Flash loan accounting trick — deposit during callback | [→](./audit-data/04-side-entrance/) |
| 05 | The Rewarder | Merkle reward bitmap accumulation bug | [→](./audit-data/05-the-rewarder/) |
| 06 | Selfie | Flash loan governance attack via current-vote checkpoint | [→](./audit-data/06-selfie/) |
| 07 | Compromised | Leaked oracle reporter private keys — median price manipulation | [→](./audit-data/07-compromised/) |
| 08 | Puppet | Uniswap V1 spot price oracle manipulation | [→](./audit-data/08-puppet/) |
| 09 | Puppet V2 | Uniswap V2 reserve ratio oracle manipulation | [→](./audit-data/09-puppet-v2/) |
| 10 | Free Rider | Payment-order bug + Uniswap V2 flash swap | [→](./audit-data/10-free-rider/) |
| 11 | Backdoor | Gnosis Safe setup() delegatecall hijack via WalletRegistry | [→](./audit-data/11-backdoor/) |
| 12 | Climber | Execute-before-check timelock + UUPS upgrade drain | [→](./audit-data/12-climber/) |
| 13 | Wallet Mining | Storage slot collision + CREATE2 prediction + Safe tx signing | [→](./audit-data/13-wallet-mining/) |
| 14 | Puppet V3 | Uniswap V3 TWAP oracle manipulation via time-weighted price crash | [→](./audit-data/14-puppet-v3/) |
| 15 | ABI Smuggling | Hardcoded calldata offset bypass — selector spoofing | [→](./audit-data/15-abi-smuggling/) |
| 16 | Shards | Precision loss / rounding exploit in fixed-point math | [→](./audit-data/16-shards/) |
| 17 | Curvy Puppet | Curve stableswap pool manipulation | [→](./audit-data/17-curvy-puppet/) |
| 18 | Withdrawal | L2 bridge Merkle proof exploit | [→](./audit-data/18-withdrawal/) |

---

## Repository structure

```
audit-data/               ← full audit reports for each challenge
│   ├── 01-unstoppable/
│   │   └── README.md     ← vulnerability description, impact, PoC, mitigation
│   ├── 02-naive-receiver/
│   └── ...
test/                     ← Foundry exploit tests (solutions)
│   ├── unstoppable/
│   ├── naive-receiver/
│   └── ...
src/                      ← original DVDF v4 contracts (unmodified)
```

---

## Vulnerability classes covered

```
flash loan attacks        →  reentrancy · accounting tricks · callback exploitation
oracle manipulation       →  spot price · reserve ratio · TWAP · reporter key compromise
governance attacks        →  flash loan voting · execute-before-check timelocks
proxy vulnerabilities     →  storage slot collision · UUPS upgrade hijacking · delegatecall backdoors
EVM internals             →  ABI encoding · calldata offset · CREATE2 prediction
signature exploits        →  ERC-2771 spoofing · EIP-712 Safe transaction signing
DeFi mechanics            →  AMM pricing · flash swaps · Merkle distributions · L2 bridges
```

---

## Tools used

![Foundry](https://img.shields.io/badge/Foundry-black?style=flat-square)
![Slither](https://img.shields.io/badge/Slither-grey?style=flat-square)
![Aderyn](https://img.shields.io/badge/Aderyn-purple?style=flat-square)

---

## Setup

```bash
git clone https://github.com/Oladayo-Ahmod/dvdf-solutions
cd dvdf-solutions
cp .env.sample .env  # add MAINNET_FORKING_URL for challenges that fork mainnet
forge install
forge build
```

Run a specific challenge:

```bash
forge test --match-contract <ChallengeName> -vvvv
```

---

## About

Built by **0xSpectreSec** (Oladayo Ahmod) — smart contract security researcher from Nigeria.
Every challenge includes a full audit-style writeup with vulnerability description, impact, PoC, and recommended mitigation.

[![X](https://img.shields.io/badge/X-@0xSpectreSec-black?style=flat-square&logo=x)](https://twitter.com/0xSpectreSec)
[![Portfolio](https://img.shields.io/badge/Portfolio-0xSpectreSec-purple?style=flat-square)](https://github.com/Oladayo-Ahmod/0xSpectreSec-audit-portfolio)
