
[<img width="200" alt="get in touch with Consensys Diligence" src="https://user-images.githubusercontent.com/2865694/56826101-91dcf380-685b-11e9-937c-af49c2510aa0.png">](https://consensys.io/diligence)<br/>
<sup>
[[  🌐  ](https://consensys.io/diligence)  [  📩  ](mailto:diligence@consensys.net)  [  🔥  ](https://consensys.io/diligence/tools/)]
</sup><br/><br/>



# Solidity Metrics for 'CLI'

## Table of contents

- [Scope](#t-scope)
    - [Source Units in Scope](#t-source-Units-in-Scope)
        - [Deployable Logic Contracts](#t-deployable-contracts)
    - [Out of Scope](#t-out-of-scope)
        - [Excluded Source Units](#t-out-of-scope-excluded-source-units)
        - [Duplicate Source Units](#t-out-of-scope-duplicate-source-units)
        - [Doppelganger Contracts](#t-out-of-scope-doppelganger-contracts)
- [Report Overview](#t-report)
    - [Risk Summary](#t-risk)
    - [Source Lines](#t-source-lines)
    - [Inline Documentation](#t-inline-documentation)
    - [Components](#t-components)
    - [Exposed Functions](#t-exposed-functions)
    - [StateVariables](#t-statevariables)
    - [Capabilities](#t-capabilities)
    - [Dependencies](#t-package-imports)
    - [Totals](#t-totals)

## <span id=t-scope>Scope</span>

This section lists files that are in scope for the metrics report. 

- **Project:** `'CLI'`
- **Included Files:** 
    - ``
- **Excluded Paths:** 
    - ``
- **File Limit:** `undefined`
    - **Exclude File list Limit:** `undefined`

- **Workspace Repository:** `unknown` (`undefined`@`undefined`)

### <span id=t-source-Units-in-Scope>Source Units in Scope</span>

Source Units Analyzed: **`4`**<br>
Source Units in Scope: **`4`** (**100%**)

| Type | File   | Logic Contracts | Interfaces | Lines | nLines | nSLOC | Comment Lines | Complex. Score | Capabilities |
| ---- | ------ | --------------- | ---------- | ----- | ------ | ----- | ------------- | -------------- | ------------ | 
| 📝 | src/naive-receiver/NaiveReceiverPool.sol | 1 | **** | 93 | 90 | 65 | 6 | 60 | **<abbr title='Payable Functions'>💰</abbr><abbr title='Initiates ETH Value Transfer'>📤</abbr><abbr title='Uses Hash-Functions'>🧮</abbr>** |
| 🎨 | src/naive-receiver/Multicall.sol | 1 | **** | 16 | 12 | 8 | 2 | 23 | **** |
| 📝 | src/naive-receiver/FlashLoanReceiver.sol | 1 | **** | 44 | 41 | 26 | 5 | 32 | **<abbr title='Uses Assembly'>🖥</abbr><abbr title='Uses Hash-Functions'>🧮</abbr><abbr title='Unchecked Blocks'>Σ</abbr>** |
| 📝🔍 | src/naive-receiver/BasicForwarder.sol | 1 | 1 | 104 | 101 | 75 | 12 | 68 | **<abbr title='Uses Assembly'>🖥</abbr><abbr title='Payable Functions'>💰</abbr><abbr title='Uses Hash-Functions'>🧮</abbr><abbr title='doppelganger(IHasTrustedForwarder)'>🔆</abbr>** |
| 📝🔍🎨 | **Totals** | **4** | **1** | **257**  | **244** | **174** | **25** | **183** | **<abbr title='Uses Assembly'>🖥</abbr><abbr title='Payable Functions'>💰</abbr><abbr title='Initiates ETH Value Transfer'>📤</abbr><abbr title='Uses Hash-Functions'>🧮</abbr><abbr title='doppelganger'>🔆</abbr><abbr title='Unchecked Blocks'>Σ</abbr>** |

<sub>
Legend: <a onclick="toggleVisibility('table-legend', this)">[➕]</a>
<div id="table-legend" style="display:none">

<ul>
<li> <b>Lines</b>: total lines of the source unit </li>
<li> <b>nLines</b>: normalized lines of the source unit (e.g. normalizes functions spanning multiple lines) </li>
<li> <b>nSLOC</b>: normalized source lines of code (only source-code lines; no comments, no blank lines) </li>
<li> <b>Comment Lines</b>: lines containing single or block comments </li>
<li> <b>Complexity Score</b>: a custom complexity score derived from code statements that are known to introduce code complexity (branches, loops, calls, external interfaces, ...) </li>
</ul>

</div>
</sub>


##### <span id=t-deployable-contracts>Deployable Logic Contracts</span>
Total: 3
* 📝 `NaiveReceiverPool`
* 📝 `FlashLoanReceiver`
* 📝 `BasicForwarder`



#### <span id=t-out-of-scope>Out of Scope</span>

##### <span id=t-out-of-scope-excluded-source-units>Excluded Source Units</span>

Source Units Excluded: **`0`**

<a onclick="toggleVisibility('excluded-files', this)">[➕]</a>
<div id="excluded-files" style="display:none">
| File   |
| ------ |
| None |

</div>


##### <span id=t-out-of-scope-duplicate-source-units>Duplicate Source Units</span>

Duplicate Source Units Excluded: **`0`** 

<a onclick="toggleVisibility('duplicate-files', this)">[➕]</a>
<div id="duplicate-files" style="display:none">
| File   |
| ------ |
| None |

</div>

##### <span id=t-out-of-scope-doppelganger-contracts>Doppelganger Contracts</span>

Doppelganger Contracts: **`1`** 

<a onclick="toggleVisibility('doppelganger-contracts', this)">[➕]</a>
<div id="doppelganger-contracts" style="display:none">
| File   | Contract | Doppelganger | 
| ------ | -------- | ------------ |
| src/naive-receiver/BasicForwarder.sol | IHasTrustedForwarder | (fuzzy) [0](https://github.com/smartcontractkit/chainlink/blob/0.8.0/evm-contracts/src/v0.4/interfaces/PointerInterface.sol), [1](https://github.com/smartcontractkit/chainlink/blob/0.8.0/evm-contracts/src/v0.5/interfaces/PointerInterface.sol), [2](https://github.com/smartcontractkit/chainlink/blob/0.8.0/evm-contracts/src/v0.6/interfaces/PointerInterface.sol), [3](https://github.com/smartcontractkit/chainlink/blob/chores-explorer-tags-for-dockerhub/evm/contracts/interfaces/PointerInterface.sol), [4](https://github.com/smartcontractkit/chainlink/blob/chores-explorer-tags-for-dockerhub/evm/v0.5/contracts/interfaces/PointerInterface.sol), [5](https://github.com/smartcontractkit/chainlink/blob/chores-v0.0.1/evm/contracts/interfaces/PointerInterface.sol), [6](https://github.com/smartcontractkit/chainlink/blob/chores-v0.0.1/evm/v0.5/contracts/interfaces/PointerInterface.sol), [7](https://github.com/smartcontractkit/chainlink/blob/explorer-v0.0.1/evm/contracts/interfaces/PointerInterface.sol), [8](https://github.com/smartcontractkit/chainlink/blob/explorer-v0.0.1/evm/v0.5/contracts/interfaces/PointerInterface.sol), [9](https://github.com/smartcontractkit/chainlink/blob/explorer-v0.7.0/evm/contracts/interfaces/PointerInterface.sol), [10](https://github.com/smartcontractkit/chainlink/blob/explorer-v0.7.0/evm/v0.5/contracts/interfaces/PointerInterface.sol), [11](https://github.com/smartcontractkit/chainlink/blob/explorer-v0.8.0/evm-contracts/src/v0.4/interfaces/PointerInterface.sol), [12](https://github.com/smartcontractkit/chainlink/blob/explorer-v0.8.0/evm-contracts/src/v0.5/interfaces/PointerInterface.sol), [13](https://github.com/smartcontractkit/chainlink/blob/explorer-v0.8.0/evm-contracts/src/v0.6/interfaces/PointerInterface.sol), [14](https://github.com/smartcontractkit/chainlink/blob/explorer-v0.8.1/evm-contracts/src/v0.4/interfaces/PointerInterface.sol), [15](https://github.com/smartcontractkit/chainlink/blob/explorer-v0.8.1/evm-contracts/src/v0.5/interfaces/PointerInterface.sol), [16](https://github.com/smartcontractkit/chainlink/blob/explorer-v0.8.1/evm-contracts/src/v0.6/interfaces/PointerInterface.sol), [17](https://github.com/smartcontractkit/chainlink/blob/explorer-v0.8.2/evm-contracts/src/v0.4/interfaces/PointerInterface.sol), [18](https://github.com/smartcontractkit/chainlink/blob/explorer-v0.8.2/evm-contracts/src/v0.5/interfaces/PointerInterface.sol), [19](https://github.com/smartcontractkit/chainlink/blob/explorer-v0.8.2/evm-contracts/src/v0.6/interfaces/PointerInterface.sol), [20](https://github.com/smartcontractkit/chainlink/blob/explorer-v0.8.3/evm-contracts/src/v0.4/interfaces/PointerInterface.sol), [21](https://github.com/smartcontractkit/chainlink/blob/explorer-v0.8.3/evm-contracts/src/v0.5/interfaces/PointerInterface.sol), [22](https://github.com/smartcontractkit/chainlink/blob/explorer-v0.8.3/evm-contracts/src/v0.6/interfaces/PointerInterface.sol), [23](https://github.com/smartcontractkit/chainlink/blob/explorer-v0.8.4/evm-contracts/src/v0.4/interfaces/PointerInterface.sol), [24](https://github.com/smartcontractkit/chainlink/blob/explorer-v0.8.4/evm-contracts/src/v0.5/interfaces/PointerInterface.sol), [25](https://github.com/smartcontractkit/chainlink/blob/explorer-v0.8.4/evm-contracts/src/v0.6/interfaces/PointerInterface.sol), [26](https://github.com/smartcontractkit/chainlink/blob/explorer-v0.8.5/evm-contracts/src/v0.4/interfaces/PointerInterface.sol), [27](https://github.com/smartcontractkit/chainlink/blob/explorer-v0.8.5/evm-contracts/src/v0.5/interfaces/PointerInterface.sol), [28](https://github.com/smartcontractkit/chainlink/blob/explorer-v0.8.5/evm-contracts/src/v0.6/interfaces/PointerInterface.sol), [29](https://github.com/smartcontractkit/chainlink/blob/upgrade/evm-contracts/src/v0.4/interfaces/PointerInterface.sol), [30](https://github.com/smartcontractkit/chainlink/blob/upgrade/evm-contracts/src/v0.5/interfaces/PointerInterface.sol), [31](https://github.com/smartcontractkit/chainlink/blob/upgrade/evm-contracts/src/v0.6/interfaces/PointerInterface.sol), [32](https://github.com/smartcontractkit/chainlink/blob/upgrade/evm-contracts/src/v0.7/interfaces/PointerInterface.sol), [33](https://github.com/smartcontractkit/chainlink/blob/v.0.8.12/evm-contracts/src/v0.4/interfaces/PointerInterface.sol), [34](https://github.com/smartcontractkit/chainlink/blob/v.0.8.12/evm-contracts/src/v0.5/interfaces/PointerInterface.sol), [35](https://github.com/smartcontractkit/chainlink/blob/v.0.8.12/evm-contracts/src/v0.6/interfaces/PointerInterface.sol), [36](https://github.com/smartcontractkit/chainlink/blob/v0.6.0/evm/contracts/interfaces/PointerInterface.sol), [37](https://github.com/smartcontractkit/chainlink/blob/v0.6.0/examples/testnet/contracts/Aggregator.sol), [38](https://github.com/smartcontractkit/chainlink/blob/v0.6.09/evm/contracts/interfaces/PointerInterface.sol), [39](https://github.com/smartcontractkit/chainlink/blob/v0.6.09/evm/v0.5/contracts/interfaces/PointerInterface.sol), [40](https://github.com/smartcontractkit/chainlink/blob/v0.6.1/evm/contracts/interfaces/PointerInterface.sol), [41](https://github.com/smartcontractkit/chainlink/blob/v0.6.1/examples/testnet/contracts/Aggregator.sol), [42](https://github.com/smartcontractkit/chainlink/blob/v0.6.10/evm/contracts/interfaces/PointerInterface.sol), [43](https://github.com/smartcontractkit/chainlink/blob/v0.6.10/evm/v0.5/contracts/interfaces/PointerInterface.sol), [44](https://github.com/smartcontractkit/chainlink/blob/v0.6.2/evm/contracts/interfaces/PointerInterface.sol), [45](https://github.com/smartcontractkit/chainlink/blob/v0.6.2/examples/testnet/contracts/Aggregator.sol), [46](https://github.com/smartcontractkit/chainlink/blob/v0.6.3/evm/contracts/interfaces/PointerInterface.sol), [47](https://github.com/smartcontractkit/chainlink/blob/v0.6.3/examples/testnet/contracts/Aggregator.sol), [48](https://github.com/smartcontractkit/chainlink/blob/v0.6.4/evm/contracts/interfaces/PointerInterface.sol), [49](https://github.com/smartcontractkit/chainlink/blob/v0.6.4/examples/testnet/contracts/Aggregator.sol), [50](https://github.com/smartcontractkit/chainlink/blob/v0.6.6/evm/contracts/interfaces/PointerInterface.sol), [51](https://github.com/smartcontractkit/chainlink/blob/v0.6.6/evm/v0.5/contracts/interfaces/PointerInterface.sol), [52](https://github.com/smartcontractkit/chainlink/blob/v0.6.7/evm/contracts/interfaces/PointerInterface.sol), [53](https://github.com/smartcontractkit/chainlink/blob/v0.6.7/evm/v0.5/contracts/interfaces/PointerInterface.sol), [54](https://github.com/smartcontractkit/chainlink/blob/v0.6.8/evm/contracts/interfaces/PointerInterface.sol), [55](https://github.com/smartcontractkit/chainlink/blob/v0.6.8/evm/v0.5/contracts/interfaces/PointerInterface.sol), [56](https://github.com/smartcontractkit/chainlink/blob/v0.6.9/evm/contracts/interfaces/PointerInterface.sol), [57](https://github.com/smartcontractkit/chainlink/blob/v0.6.9/evm/v0.5/contracts/interfaces/PointerInterface.sol), [58](https://github.com/smartcontractkit/chainlink/blob/v0.7.0/evm/contracts/interfaces/PointerInterface.sol), [59](https://github.com/smartcontractkit/chainlink/blob/v0.7.0/evm/v0.5/contracts/interfaces/PointerInterface.sol), [60](https://github.com/smartcontractkit/chainlink/blob/v0.7.1/evm/contracts/interfaces/PointerInterface.sol), [61](https://github.com/smartcontractkit/chainlink/blob/v0.7.1/evm/v0.5/contracts/interfaces/PointerInterface.sol), [62](https://github.com/smartcontractkit/chainlink/blob/v0.7.2/evm/contracts/interfaces/PointerInterface.sol), [63](https://github.com/smartcontractkit/chainlink/blob/v0.7.2/evm/v0.5/contracts/interfaces/PointerInterface.sol), [64](https://github.com/smartcontractkit/chainlink/blob/v0.7.3/evm/contracts/interfaces/PointerInterface.sol), [65](https://github.com/smartcontractkit/chainlink/blob/v0.7.3/evm/v0.5/contracts/interfaces/PointerInterface.sol), [66](https://github.com/smartcontractkit/chainlink/blob/v0.7.4/evm-contracts/src/v0.4/interfaces/PointerInterface.sol), [67](https://github.com/smartcontractkit/chainlink/blob/v0.7.4/evm-contracts/src/v0.5/interfaces/PointerInterface.sol), [68](https://github.com/smartcontractkit/chainlink/blob/v0.7.4/evm-contracts/src/v0.6/interfaces/PointerInterface.sol), [69](https://github.com/smartcontractkit/chainlink/blob/v0.7.5/evm-contracts/src/v0.4/interfaces/PointerInterface.sol), [70](https://github.com/smartcontractkit/chainlink/blob/v0.7.5/evm-contracts/src/v0.5/interfaces/PointerInterface.sol), [71](https://github.com/smartcontractkit/chainlink/blob/v0.7.5/evm-contracts/src/v0.6/interfaces/PointerInterface.sol), [72](https://github.com/smartcontractkit/chainlink/blob/v0.7.6/evm-contracts/src/v0.4/interfaces/PointerInterface.sol), [73](https://github.com/smartcontractkit/chainlink/blob/v0.7.6/evm-contracts/src/v0.5/interfaces/PointerInterface.sol), [74](https://github.com/smartcontractkit/chainlink/blob/v0.7.6/evm-contracts/src/v0.6/interfaces/PointerInterface.sol), [75](https://github.com/smartcontractkit/chainlink/blob/v0.7.7/evm-contracts/src/v0.4/interfaces/PointerInterface.sol), [76](https://github.com/smartcontractkit/chainlink/blob/v0.7.7/evm-contracts/src/v0.5/interfaces/PointerInterface.sol), [77](https://github.com/smartcontractkit/chainlink/blob/v0.7.7/evm-contracts/src/v0.6/interfaces/PointerInterface.sol), [78](https://github.com/smartcontractkit/chainlink/blob/v0.7.8/evm-contracts/src/v0.4/interfaces/PointerInterface.sol), [79](https://github.com/smartcontractkit/chainlink/blob/v0.7.8/evm-contracts/src/v0.5/interfaces/PointerInterface.sol), [80](https://github.com/smartcontractkit/chainlink/blob/v0.7.8/evm-contracts/src/v0.6/interfaces/PointerInterface.sol), [81](https://github.com/smartcontractkit/chainlink/blob/v0.8.0/evm-contracts/src/v0.4/interfaces/PointerInterface.sol), [82](https://github.com/smartcontractkit/chainlink/blob/v0.8.0/evm-contracts/src/v0.5/interfaces/PointerInterface.sol), [83](https://github.com/smartcontractkit/chainlink/blob/v0.8.0/evm-contracts/src/v0.6/interfaces/PointerInterface.sol), [84](https://github.com/smartcontractkit/chainlink/blob/v0.8.1/evm-contracts/src/v0.4/interfaces/PointerInterface.sol), [85](https://github.com/smartcontractkit/chainlink/blob/v0.8.1/evm-contracts/src/v0.5/interfaces/PointerInterface.sol), [86](https://github.com/smartcontractkit/chainlink/blob/v0.8.1/evm-contracts/src/v0.6/interfaces/PointerInterface.sol), [87](https://github.com/smartcontractkit/chainlink/blob/v0.8.10/evm-contracts/src/v0.4/interfaces/PointerInterface.sol), [88](https://github.com/smartcontractkit/chainlink/blob/v0.8.10/evm-contracts/src/v0.5/interfaces/PointerInterface.sol), [89](https://github.com/smartcontractkit/chainlink/blob/v0.8.10/evm-contracts/src/v0.6/interfaces/PointerInterface.sol), [90](https://github.com/smartcontractkit/chainlink/blob/v0.8.11/evm-contracts/src/v0.4/interfaces/PointerInterface.sol), [91](https://github.com/smartcontractkit/chainlink/blob/v0.8.11/evm-contracts/src/v0.5/interfaces/PointerInterface.sol), [92](https://github.com/smartcontractkit/chainlink/blob/v0.8.11/evm-contracts/src/v0.6/interfaces/PointerInterface.sol), [93](https://github.com/smartcontractkit/chainlink/blob/v0.8.12/evm-contracts/src/v0.4/interfaces/PointerInterface.sol), [94](https://github.com/smartcontractkit/chainlink/blob/v0.8.12/evm-contracts/src/v0.5/interfaces/PointerInterface.sol), [95](https://github.com/smartcontractkit/chainlink/blob/v0.8.12/evm-contracts/src/v0.6/interfaces/PointerInterface.sol), [96](https://github.com/smartcontractkit/chainlink/blob/v0.8.13/evm-contracts/src/v0.4/interfaces/PointerInterface.sol), [97](https://github.com/smartcontractkit/chainlink/blob/v0.8.13/evm-contracts/src/v0.5/interfaces/PointerInterface.sol), [98](https://github.com/smartcontractkit/chainlink/blob/v0.8.13/evm-contracts/src/v0.6/interfaces/PointerInterface.sol), [99](https://github.com/smartcontractkit/chainlink/blob/v0.8.14/evm-contracts/src/v0.4/interfaces/PointerInterface.sol), [100](https://github.com/smartcontractkit/chainlink/blob/v0.8.14/evm-contracts/src/v0.5/interfaces/PointerInterface.sol), [101](https://github.com/smartcontractkit/chainlink/blob/v0.8.14/evm-contracts/src/v0.6/interfaces/PointerInterface.sol), [102](https://github.com/smartcontractkit/chainlink/blob/v0.8.15/evm-contracts/src/v0.4/interfaces/PointerInterface.sol), [103](https://github.com/smartcontractkit/chainlink/blob/v0.8.15/evm-contracts/src/v0.5/interfaces/PointerInterface.sol), [104](https://github.com/smartcontractkit/chainlink/blob/v0.8.15/evm-contracts/src/v0.6/interfaces/PointerInterface.sol), [105](https://github.com/smartcontractkit/chainlink/blob/v0.8.16/evm-contracts/src/v0.4/interfaces/PointerInterface.sol), [106](https://github.com/smartcontractkit/chainlink/blob/v0.8.16/evm-contracts/src/v0.5/interfaces/PointerInterface.sol), [107](https://github.com/smartcontractkit/chainlink/blob/v0.8.16/evm-contracts/src/v0.6/interfaces/PointerInterface.sol), [108](https://github.com/smartcontractkit/chainlink/blob/v0.8.17/evm-contracts/src/v0.4/interfaces/PointerInterface.sol), [109](https://github.com/smartcontractkit/chainlink/blob/v0.8.17/evm-contracts/src/v0.5/interfaces/PointerInterface.sol), [110](https://github.com/smartcontractkit/chainlink/blob/v0.8.17/evm-contracts/src/v0.6/interfaces/PointerInterface.sol), [111](https://github.com/smartcontractkit/chainlink/blob/v0.8.18/evm-contracts/src/v0.4/interfaces/PointerInterface.sol), [112](https://github.com/smartcontractkit/chainlink/blob/v0.8.18/evm-contracts/src/v0.5/interfaces/PointerInterface.sol), [113](https://github.com/smartcontractkit/chainlink/blob/v0.8.18/evm-contracts/src/v0.6/interfaces/PointerInterface.sol), [114](https://github.com/smartcontractkit/chainlink/blob/v0.8.2/evm-contracts/src/v0.4/interfaces/PointerInterface.sol), [115](https://github.com/smartcontractkit/chainlink/blob/v0.8.2/evm-contracts/src/v0.5/interfaces/PointerInterface.sol), [116](https://github.com/smartcontractkit/chainlink/blob/v0.8.2/evm-contracts/src/v0.6/interfaces/PointerInterface.sol), [117](https://github.com/smartcontractkit/chainlink/blob/v0.8.3/evm-contracts/src/v0.4/interfaces/PointerInterface.sol), [118](https://github.com/smartcontractkit/chainlink/blob/v0.8.3/evm-contracts/src/v0.5/interfaces/PointerInterface.sol), [119](https://github.com/smartcontractkit/chainlink/blob/v0.8.3/evm-contracts/src/v0.6/interfaces/PointerInterface.sol), [120](https://github.com/smartcontractkit/chainlink/blob/v0.8.4/evm-contracts/src/v0.4/interfaces/PointerInterface.sol), [121](https://github.com/smartcontractkit/chainlink/blob/v0.8.4/evm-contracts/src/v0.5/interfaces/PointerInterface.sol), [122](https://github.com/smartcontractkit/chainlink/blob/v0.8.4/evm-contracts/src/v0.6/interfaces/PointerInterface.sol), [123](https://github.com/smartcontractkit/chainlink/blob/v0.8.5/evm-contracts/src/v0.4/interfaces/PointerInterface.sol), [124](https://github.com/smartcontractkit/chainlink/blob/v0.8.5/evm-contracts/src/v0.5/interfaces/PointerInterface.sol), [125](https://github.com/smartcontractkit/chainlink/blob/v0.8.5/evm-contracts/src/v0.6/interfaces/PointerInterface.sol), [126](https://github.com/smartcontractkit/chainlink/blob/v0.8.6/evm-contracts/src/v0.4/interfaces/PointerInterface.sol), [127](https://github.com/smartcontractkit/chainlink/blob/v0.8.6/evm-contracts/src/v0.5/interfaces/PointerInterface.sol), [128](https://github.com/smartcontractkit/chainlink/blob/v0.8.6/evm-contracts/src/v0.6/interfaces/PointerInterface.sol), [129](https://github.com/smartcontractkit/chainlink/blob/v0.8.7/evm-contracts/src/v0.4/interfaces/PointerInterface.sol), [130](https://github.com/smartcontractkit/chainlink/blob/v0.8.7/evm-contracts/src/v0.5/interfaces/PointerInterface.sol), [131](https://github.com/smartcontractkit/chainlink/blob/v0.8.7/evm-contracts/src/v0.6/interfaces/PointerInterface.sol), [132](https://github.com/smartcontractkit/chainlink/blob/v0.8.8/evm-contracts/src/v0.4/interfaces/PointerInterface.sol), [133](https://github.com/smartcontractkit/chainlink/blob/v0.8.8/evm-contracts/src/v0.5/interfaces/PointerInterface.sol), [134](https://github.com/smartcontractkit/chainlink/blob/v0.8.8/evm-contracts/src/v0.6/interfaces/PointerInterface.sol), [135](https://github.com/smartcontractkit/chainlink/blob/v0.8.9/evm-contracts/src/v0.4/interfaces/PointerInterface.sol), [136](https://github.com/smartcontractkit/chainlink/blob/v0.8.9/evm-contracts/src/v0.5/interfaces/PointerInterface.sol), [137](https://github.com/smartcontractkit/chainlink/blob/v0.8.9/evm-contracts/src/v0.6/interfaces/PointerInterface.sol), [138](https://github.com/smartcontractkit/chainlink/blob/v0.9.0/evm-contracts/src/v0.4/interfaces/PointerInterface.sol), [139](https://github.com/smartcontractkit/chainlink/blob/v0.9.0/evm-contracts/src/v0.5/interfaces/PointerInterface.sol), [140](https://github.com/smartcontractkit/chainlink/blob/v0.9.0/evm-contracts/src/v0.6/interfaces/PointerInterface.sol), [141](https://github.com/smartcontractkit/chainlink/blob/v0.9.2/evm-contracts/src/v0.4/interfaces/PointerInterface.sol), [142](https://github.com/smartcontractkit/chainlink/blob/v0.9.2/evm-contracts/src/v0.5/interfaces/PointerInterface.sol), [143](https://github.com/smartcontractkit/chainlink/blob/v0.9.2/evm-contracts/src/v0.6/interfaces/PointerInterface.sol), [144](https://github.com/smartcontractkit/chainlink/blob/v0.9.3/evm-contracts/src/v0.4/interfaces/PointerInterface.sol), [145](https://github.com/smartcontractkit/chainlink/blob/v0.9.3/evm-contracts/src/v0.5/interfaces/PointerInterface.sol), [146](https://github.com/smartcontractkit/chainlink/blob/v0.9.3/evm-contracts/src/v0.6/interfaces/PointerInterface.sol), [147](https://github.com/smartcontractkit/chainlink/blob/v0.9.4/evm-contracts/src/v0.4/interfaces/PointerInterface.sol), [148](https://github.com/smartcontractkit/chainlink/blob/v0.9.4/evm-contracts/src/v0.5/interfaces/PointerInterface.sol), [149](https://github.com/smartcontractkit/chainlink/blob/v0.9.4/evm-contracts/src/v0.6/interfaces/PointerInterface.sol), [150](https://github.com/smartcontractkit/chainlink/blob/v0.9.5/evm-contracts/src/v0.4/interfaces/PointerInterface.sol), [151](https://github.com/smartcontractkit/chainlink/blob/v0.9.5/evm-contracts/src/v0.5/interfaces/PointerInterface.sol), [152](https://github.com/smartcontractkit/chainlink/blob/v0.9.5/evm-contracts/src/v0.6/interfaces/PointerInterface.sol), [153](https://github.com/smartcontractkit/chainlink/blob/v0.9.6/evm-contracts/src/v0.4/interfaces/PointerInterface.sol), [154](https://github.com/smartcontractkit/chainlink/blob/v0.9.6/evm-contracts/src/v0.5/interfaces/PointerInterface.sol), [155](https://github.com/smartcontractkit/chainlink/blob/v0.9.6/evm-contracts/src/v0.6/interfaces/PointerInterface.sol), [156](https://github.com/smartcontractkit/chainlink/blob/v0.9.6/evm-contracts/src/v0.7/interfaces/PointerInterface.sol), [157](https://github.com/smartcontractkit/chainlink/blob/v0.9.7/evm-contracts/src/v0.4/interfaces/PointerInterface.sol), [158](https://github.com/smartcontractkit/chainlink/blob/v0.9.7/evm-contracts/src/v0.5/interfaces/PointerInterface.sol), [159](https://github.com/smartcontractkit/chainlink/blob/v0.9.7/evm-contracts/src/v0.6/interfaces/PointerInterface.sol), [160](https://github.com/smartcontractkit/chainlink/blob/v0.9.7/evm-contracts/src/v0.7/interfaces/PointerInterface.sol), [161](https://github.com/smartcontractkit/chainlink/blob/v0.9.8/evm-contracts/src/v0.4/interfaces/PointerInterface.sol), [162](https://github.com/smartcontractkit/chainlink/blob/v0.9.8/evm-contracts/src/v0.5/interfaces/PointerInterface.sol), [163](https://github.com/smartcontractkit/chainlink/blob/v0.9.8/evm-contracts/src/v0.6/interfaces/PointerInterface.sol), [164](https://github.com/smartcontractkit/chainlink/blob/v0.9.8/evm-contracts/src/v0.7/interfaces/PointerInterface.sol), [165](https://github.com/smartcontractkit/chainlink/blob/vtest-2020-03-03/evm-contracts/src/v0.4/interfaces/PointerInterface.sol), [166](https://github.com/smartcontractkit/chainlink/blob/vtest-2020-03-03/evm-contracts/src/v0.5/interfaces/PointerInterface.sol), [167](https://github.com/smartcontractkit/chainlink/blob/vtest-2020-03-03/evm-contracts/src/v0.6/interfaces/PointerInterface.sol), [168](https://github.com/OpenZeppelin/openzeppelin-contracts-upgradeable/blob/v4.1.0/contracts/proxy/beacon/IBeaconUpgradeable.sol), [169](https://github.com/OpenZeppelin/openzeppelin-contracts-upgradeable/blob/v4.1.0-rc.0/contracts/proxy/beacon/IBeaconUpgradeable.sol), [170](https://github.com/OpenZeppelin/openzeppelin-contracts-upgradeable/blob/v4.2.0/contracts/proxy/beacon/IBeaconUpgradeable.sol) |

</div>


## <span id=t-report>Report</span>

### Overview

The analysis finished with **`0`** errors and **`0`** duplicate files.





#### <span id=t-risk>Risk</span>

<div class="wrapper" style="max-width: 512px; margin: auto">
			<canvas id="chart-risk-summary"></canvas>
</div>

#### <span id=t-source-lines>Source Lines (sloc vs. nsloc)</span>

<div class="wrapper" style="max-width: 512px; margin: auto">
    <canvas id="chart-nsloc-total"></canvas>
</div>

#### <span id=t-inline-documentation>Inline Documentation</span>

- **Comment-to-Source Ratio:** On average there are`7.44` code lines per comment (lower=better).
- **ToDo's:** `0` 

#### <span id=t-components>Components</span>

| 📝Contracts   | 📚Libraries | 🔍Interfaces | 🎨Abstract |
| ------------- | ----------- | ------------ | ---------- |
| 3 | 0  | 1  | 1 |

#### <span id=t-exposed-functions>Exposed Functions</span>

This section lists functions that are explicitly declared public or payable. Please note that getter methods for public stateVars are not included.  

| 🌐Public   | 💰Payable |
| ---------- | --------- |
| 12 | 3  | 

| External   | Internal | Private | Pure | View |
| ---------- | -------- | ------- | ---- | ---- |
| 10 | 10  | 2 | 3 | 6 |

#### <span id=t-statevariables>StateVariables</span>

| Total      | 🌐Public  |
| ---------- | --------- |
| 10  | 6 |

#### <span id=t-capabilities>Capabilities</span>

| Solidity Versions observed | 🧪 Experimental Features | 💰 Can Receive Funds | 🖥 Uses Assembly | 💣 Has Destroyable Contracts | 
| -------------------------- | ------------------------ | -------------------- | ---------------- | ---------------------------- |
| `=0.8.25` |  | `yes` | `yes` <br/>(3 asm blocks) | **** | 

| 📤 Transfers ETH | ⚡ Low-Level Calls | 👥 DelegateCall | 🧮 Uses Hash Functions | 🔖 ECRecover | 🌀 New/Create/Create2 |
| ---------------- | ----------------- | --------------- | ---------------------- | ------------ | --------------------- |
| `yes` | **** | **** | `yes` | **** | **** | 

| ♻️ TryCatch | Σ Unchecked |
| ---------- | ----------- |
| **** | `yes` |

#### <span id=t-package-imports>Dependencies / External Imports</span>

| Dependency / Import Path | Count  | 
| ------------------------ | ------ |
| @openzeppelin/contracts/interfaces/IERC3156FlashBorrower.sol | 2 |
| @openzeppelin/contracts/interfaces/IERC3156FlashLender.sol | 1 |
| @openzeppelin/contracts/utils/Address.sol | 2 |
| @openzeppelin/contracts/utils/Context.sol | 1 |
| @openzeppelin/contracts/utils/cryptography/ECDSA.sol | 1 |
| solady/utils/EIP712.sol | 1 |
| solmate/tokens/WETH.sol | 1 |

#### <span id=t-totals>Totals</span>

##### Summary

<div class="wrapper" style="max-width: 90%; margin: auto">
    <canvas id="chart-num-bar"></canvas>
</div>

##### AST Node Statistics

###### Function Calls

<div class="wrapper" style="max-width: 90%; margin: auto">
    <canvas id="chart-num-bar-ast-funccalls"></canvas>
</div>

###### Assembly Calls

<div class="wrapper" style="max-width: 90%; margin: auto">
    <canvas id="chart-num-bar-ast-asmcalls"></canvas>
</div>

###### AST Total

<div class="wrapper" style="max-width: 90%; margin: auto">
    <canvas id="chart-num-bar-ast"></canvas>
</div>

##### Inheritance Graph

<a onclick="toggleVisibility('surya-inherit', this)">[➕]</a>
<div id="surya-inherit" style="display:none">
<div class="wrapper" style="max-width: 512px; margin: auto">
    <div id="surya-inheritance" style="text-align: center;"></div> 
</div>
</div>

##### CallGraph

<a onclick="toggleVisibility('surya-call', this)">[➕]</a>
<div id="surya-call" style="display:none">
<div class="wrapper" style="max-width: 512px; margin: auto">
    <div id="surya-callgraph" style="text-align: center;"></div>
</div>
</div>

###### Contract Summary

<a onclick="toggleVisibility('surya-mdreport', this)">[➕]</a>
<div id="surya-mdreport" style="display:none">
 

 Files Description Table


|  File Name  |  SHA-1 Hash  |
|-------------|--------------|
| src/naive-receiver/NaiveReceiverPool.sol | f890352d73fd56ca3aeefdc5b7b12873ba8b95b2 |
| src/naive-receiver/Multicall.sol | e06bc10e394f252b90cea93f16acbed73a4807bd |
| src/naive-receiver/FlashLoanReceiver.sol | 2207a521486c470d3187d539487fb23af53d31f5 |
| src/naive-receiver/BasicForwarder.sol | 3a6bed46ede4f59eb0edfd5c00972ba403e207eb |


 Contracts Description Table


|  Contract  |         Type        |       Bases      |                  |                 |
|:----------:|:-------------------:|:----------------:|:----------------:|:---------------:|
|     └      |  **Function Name**  |  **Visibility**  |  **Mutability**  |  **Modifiers**  |
||||||
| **NaiveReceiverPool** | Implementation | Multicall, IERC3156FlashLender |||
| └ | <Constructor> | Public ❗️ |  💵 |NO❗️ |
| └ | maxFlashLoan | External ❗️ |   |NO❗️ |
| └ | flashFee | External ❗️ |   |NO❗️ |
| └ | flashLoan | External ❗️ | 🛑  |NO❗️ |
| └ | withdraw | External ❗️ | 🛑  |NO❗️ |
| └ | deposit | External ❗️ |  💵 |NO❗️ |
| └ | _deposit | Private 🔐 | 🛑  | |
| └ | _msgSender | Internal 🔒 |   | |
||||||
| **Multicall** | Implementation | Context |||
| └ | multicall | External ❗️ | 🛑  |NO❗️ |
||||||
| **FlashLoanReceiver** | Implementation | IERC3156FlashBorrower |||
| └ | <Constructor> | Public ❗️ | 🛑  |NO❗️ |
| └ | onFlashLoan | External ❗️ | 🛑  |NO❗️ |
| └ | _executeActionDuringFlashLoan | Internal 🔒 | 🛑  | |
||||||
| **IHasTrustedForwarder** | Interface |  |||
| └ | trustedForwarder | External ❗️ |   |NO❗️ |
||||||
| **BasicForwarder** | Implementation | EIP712 |||
| └ | _checkRequest | Private 🔐 |   | |
| └ | execute | Public ❗️ |  💵 |NO❗️ |
| └ | _domainNameAndVersion | Internal 🔒 |   | |
| └ | getDataHash | Public ❗️ |   |NO❗️ |
| └ | domainSeparator | External ❗️ |   |NO❗️ |
| └ | getRequestTypehash | External ❗️ |   |NO❗️ |


 Legend

|  Symbol  |  Meaning  |
|:--------:|-----------|
|    🛑    | Function can modify state |
|    💵    | Function is payable |
 

</div>
____
<sub>
Thinking about smart contract security? We can provide training, ongoing advice, and smart contract auditing. [Contact us](https://consensys.io/diligence/contact/).
</sub>


