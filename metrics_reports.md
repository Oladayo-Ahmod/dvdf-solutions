
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

Source Units Analyzed: **`5`**<br>
Source Units in Scope: **`5`** (**100%**)

| Type | File   | Logic Contracts | Interfaces | Lines | nLines | nSLOC | Comment Lines | Complex. Score | Capabilities |
| ---- | ------ | --------------- | ---------- | ----- | ------ | ----- | ------------- | -------------- | ------------ | 
| 📝 | src/climber/ClimberVault.sol | 1 | **** | 84 | 84 | 55 | 11 | 53 | **<abbr title='create/create2'>🌀</abbr>** |
| 🎨 | src/climber/ClimberTimelockBase.sol | 1 | **** | 54 | 49 | 35 | 8 | 19 | **<abbr title='Payable Functions'>💰</abbr><abbr title='Uses Hash-Functions'>🧮</abbr>** |
| 📝 | src/climber/ClimberTimelock.sol | 1 | **** | 112 | 101 | 67 | 15 | 51 | **<abbr title='Payable Functions'>💰</abbr>** |
|  | src/climber/ClimberErrors.sol | **** | **** | 14 | 14 | 11 | 2 | **** | **** |
|  | src/climber/ClimberConstants.sol | **** | **** | 24 | 24 | 8 | 10 | **** | **** |
| 📝🎨 | **Totals** | **3** | **** | **288**  | **272** | **176** | **46** | **123** | **<abbr title='Payable Functions'>💰</abbr><abbr title='Uses Hash-Functions'>🧮</abbr><abbr title='create/create2'>🌀</abbr>** |

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
Total: 2
* 📝 `ClimberVault`
* 📝 `ClimberTimelock`



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

Doppelganger Contracts: **`0`** 

<a onclick="toggleVisibility('doppelganger-contracts', this)">[➕]</a>
<div id="doppelganger-contracts" style="display:none">
| File   | Contract | Doppelganger | 
| ------ | -------- | ------------ |


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

- **Comment-to-Source Ratio:** On average there are`4.15` code lines per comment (lower=better).
- **ToDo's:** `0` 

#### <span id=t-components>Components</span>

| 📝Contracts   | 📚Libraries | 🔍Interfaces | 🎨Abstract |
| ------------- | ----------- | ------------ | ---------- |
| 2 | 0  | 0  | 1 |

#### <span id=t-exposed-functions>Exposed Functions</span>

This section lists functions that are explicitly declared public or payable. Please note that getter methods for public stateVars are not included.  

| 🌐Public   | 💰Payable |
| ---------- | --------- |
| 11 | 2  | 

| External   | Internal | Private | Pure | View |
| ---------- | -------- | ------- | ---- | ---- |
| 9 | 11  | 2 | 1 | 3 |

#### <span id=t-statevariables>StateVariables</span>

| Total      | 🌐Public  |
| ---------- | --------- |
| 4  | 2 |

#### <span id=t-capabilities>Capabilities</span>

| Solidity Versions observed | 🧪 Experimental Features | 💰 Can Receive Funds | 🖥 Uses Assembly | 💣 Has Destroyable Contracts | 
| -------------------------- | ------------------------ | -------------------- | ---------------- | ---------------------------- |
| `=0.8.25` |  | `yes` | **** | **** | 

| 📤 Transfers ETH | ⚡ Low-Level Calls | 👥 DelegateCall | 🧮 Uses Hash Functions | 🔖 ECRecover | 🌀 New/Create/Create2 |
| ---------------- | ----------------- | --------------- | ---------------------- | ------------ | --------------------- |
| **** | **** | **** | `yes` | **** | `yes`<br>→ `NewContract:ClimberTimelock` | 

| ♻️ TryCatch | Σ Unchecked |
| ---------- | ----------- |
| **** | **** |

#### <span id=t-package-imports>Dependencies / External Imports</span>

| Dependency / Import Path | Count  | 
| ------------------------ | ------ |
| @openzeppelin/contracts-upgradeable/access/OwnableUpgradeable.sol | 1 |
| @openzeppelin/contracts-upgradeable/proxy/utils/Initializable.sol | 1 |
| @openzeppelin/contracts-upgradeable/proxy/utils/UUPSUpgradeable.sol | 1 |
| @openzeppelin/contracts/access/AccessControl.sol | 1 |
| @openzeppelin/contracts/token/ERC20/IERC20.sol | 1 |
| @openzeppelin/contracts/utils/Address.sol | 1 |
| solady/utils/SafeTransferLib.sol | 1 |

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
| src/climber/ClimberVault.sol | 4c02fcee1bf6b17fb3d1fc9a46f5007dbcc3be02 |
| src/climber/ClimberTimelockBase.sol | fd074c868b2f1823b58fe6891f78329a8983c21a |
| src/climber/ClimberTimelock.sol | 225a9cb8341c35fa224515ee84275868e6da1dee |
| src/climber/ClimberErrors.sol | c6bf807432c5363ddc797b5d14de3ca9a02fb207 |
| src/climber/ClimberConstants.sol | 7cdcdb57a65e371fdefc7fee93ef21b740b0e499 |


 Contracts Description Table


|  Contract  |         Type        |       Bases      |                  |                 |
|:----------:|:-------------------:|:----------------:|:----------------:|:---------------:|
|     └      |  **Function Name**  |  **Visibility**  |  **Mutability**  |  **Modifiers**  |
||||||
| **ClimberVault** | Implementation | Initializable, OwnableUpgradeable, UUPSUpgradeable |||
| └ | <Constructor> | Public ❗️ | 🛑  |NO❗️ |
| └ | initialize | External ❗️ | 🛑  | initializer |
| └ | withdraw | External ❗️ | 🛑  | onlyOwner |
| └ | sweepFunds | External ❗️ | 🛑  | onlySweeper |
| └ | getSweeper | External ❗️ |   |NO❗️ |
| └ | _setSweeper | Private 🔐 | 🛑  | |
| └ | getLastWithdrawalTimestamp | External ❗️ |   |NO❗️ |
| └ | _updateLastWithdrawalTimestamp | Private 🔐 | 🛑  | |
| └ | _authorizeUpgrade | Internal 🔒 | 🛑  | onlyOwner |
||||||
| **ClimberTimelockBase** | Implementation | AccessControl |||
| └ | getOperationState | Public ❗️ |   |NO❗️ |
| └ | getOperationId | Public ❗️ |   |NO❗️ |
| └ | <Receive Ether> | External ❗️ |  💵 |NO❗️ |
||||||
| **ClimberTimelock** | Implementation | ClimberTimelockBase |||
| └ | <Constructor> | Public ❗️ | 🛑  |NO❗️ |
| └ | schedule | External ❗️ | 🛑  | onlyRole |
| └ | execute | External ❗️ |  💵 |NO❗️ |
| └ | updateDelay | External ❗️ | 🛑  |NO❗️ |


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


