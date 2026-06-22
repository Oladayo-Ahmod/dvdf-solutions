
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

Source Units Analyzed: **`3`**<br>
Source Units in Scope: **`3`** (**100%**)

| Type | File   | Logic Contracts | Interfaces | Lines | nLines | nSLOC | Comment Lines | Complex. Score | Capabilities |
| ---- | ------ | --------------- | ---------- | ----- | ------ | ----- | ------------- | -------------- | ------------ | 
| 📝 | src/compromised/TrustfulOracleInitializer.sol | 1 | **** | 17 | 17 | 11 | 2 | 16 | **<abbr title='create/create2'>🌀</abbr>** |
| 📝 | src/compromised/TrustfulOracle.sol | 1 | **** | 96 | 93 | 71 | 9 | 66 | **<abbr title='Uses Hash-Functions'>🧮</abbr><abbr title='Unchecked Blocks'>Σ</abbr>** |
| 📝 | src/compromised/Exchange.sol | 1 | **** | 73 | 73 | 52 | 4 | 63 | **<abbr title='Payable Functions'>💰</abbr><abbr title='create/create2'>🌀</abbr><abbr title='Unchecked Blocks'>Σ</abbr>** |
| 📝 | **Totals** | **3** | **** | **186**  | **183** | **134** | **15** | **145** | **<abbr title='Payable Functions'>💰</abbr><abbr title='Uses Hash-Functions'>🧮</abbr><abbr title='create/create2'>🌀</abbr><abbr title='Unchecked Blocks'>Σ</abbr>** |

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
* 📝 `TrustfulOracleInitializer`
* 📝 `TrustfulOracle`
* 📝 `Exchange`



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

- **Comment-to-Source Ratio:** On average there are`9.13` code lines per comment (lower=better).
- **ToDo's:** `0` 

#### <span id=t-components>Components</span>

| 📝Contracts   | 📚Libraries | 🔍Interfaces | 🎨Abstract |
| ------------- | ----------- | ------------ | ---------- |
| 3 | 0  | 0  | 0 |

#### <span id=t-exposed-functions>Exposed Functions</span>

This section lists functions that are explicitly declared public or payable. Please note that getter methods for public stateVars are not included.  

| 🌐Public   | 💰Payable |
| ---------- | --------- |
| 8 | 3  | 

| External   | Internal | Private | Pure | View |
| ---------- | -------- | ------- | ---- | ---- |
| 6 | 6  | 2 | 0 | 4 |

#### <span id=t-statevariables>StateVariables</span>

| Total      | 🌐Public  |
| ---------- | --------- |
| 7  | 6 |

#### <span id=t-capabilities>Capabilities</span>

| Solidity Versions observed | 🧪 Experimental Features | 💰 Can Receive Funds | 🖥 Uses Assembly | 💣 Has Destroyable Contracts | 
| -------------------------- | ------------------------ | -------------------- | ---------------- | ---------------------------- |
| `=0.8.25` |  | `yes` | **** | **** | 

| 📤 Transfers ETH | ⚡ Low-Level Calls | 👥 DelegateCall | 🧮 Uses Hash Functions | 🔖 ECRecover | 🌀 New/Create/Create2 |
| ---------------- | ----------------- | --------------- | ---------------------- | ------------ | --------------------- |
| **** | **** | **** | `yes` | **** | `yes`<br>→ `NewContract:TrustfulOracle`<br/>→ `NewContract:DamnValuableNFT` | 

| ♻️ TryCatch | Σ Unchecked |
| ---------- | ----------- |
| **** | `yes` |

#### <span id=t-package-imports>Dependencies / External Imports</span>

| Dependency / Import Path | Count  | 
| ------------------------ | ------ |
| @openzeppelin/contracts/access/extensions/AccessControlEnumerable.sol | 1 |
| @openzeppelin/contracts/utils/Address.sol | 1 |
| @openzeppelin/contracts/utils/ReentrancyGuard.sol | 1 |
| solady/utils/LibSort.sol | 1 |

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
| src/compromised/TrustfulOracleInitializer.sol | 9d5e6201b0872823ce4827603a56a07b0133f999 |
| src/compromised/TrustfulOracle.sol | 0d6df4bf0715113704e93ec38781f72b79db673a |
| src/compromised/Exchange.sol | 35c3638542575d8ac84ab940a22b5b7ac4c3fc15 |


 Contracts Description Table


|  Contract  |         Type        |       Bases      |                  |                 |
|:----------:|:-------------------:|:----------------:|:----------------:|:---------------:|
|     └      |  **Function Name**  |  **Visibility**  |  **Mutability**  |  **Modifiers**  |
||||||
| **TrustfulOracleInitializer** | Implementation |  |||
| └ | <Constructor> | Public ❗️ | 🛑  |NO❗️ |
||||||
| **TrustfulOracle** | Implementation | AccessControlEnumerable |||
| └ | <Constructor> | Public ❗️ | 🛑  |NO❗️ |
| └ | setupInitialPrices | External ❗️ | 🛑  | onlyRole |
| └ | postPrice | External ❗️ | 🛑  | onlyRole |
| └ | getMedianPrice | External ❗️ |   |NO❗️ |
| └ | getAllPricesForSymbol | Public ❗️ |   |NO❗️ |
| └ | getPriceBySource | Public ❗️ |   |NO❗️ |
| └ | _setPrice | Private 🔐 | 🛑  | |
| └ | _computeMedianPrice | Private 🔐 |   | |
||||||
| **Exchange** | Implementation | ReentrancyGuard |||
| └ | <Constructor> | Public ❗️ |  💵 |NO❗️ |
| └ | buyOne | External ❗️ |  💵 | nonReentrant |
| └ | sellOne | External ❗️ | 🛑  | nonReentrant |
| └ | <Receive Ether> | External ❗️ |  💵 |NO❗️ |


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


