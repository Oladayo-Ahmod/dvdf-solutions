
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
| 📝 | src/puppet/PuppetPool.sol | 1 | **** | 63 | 63 | 42 | 5 | 28 | **<abbr title='Payable Functions'>💰</abbr><abbr title='Initiates ETH Value Transfer'>📤</abbr><abbr title='Unchecked Blocks'>Σ</abbr>** |
| 🔍 | src/puppet/IUniswapV1Factory.sol | **** | 1 | 13 | 7 | 4 | 1 | 13 | **** |
| 🔍 | src/puppet/IUniswapV1Exchange.sol | **** | 1 | 115 | 12 | 9 | 1 | 72 | **<abbr title='Payable Functions'>💰</abbr>** |
| 📝🔍 | **Totals** | **1** | **2** | **191**  | **82** | **55** | **7** | **113** | **<abbr title='Payable Functions'>💰</abbr><abbr title='Initiates ETH Value Transfer'>📤</abbr><abbr title='Unchecked Blocks'>Σ</abbr>** |

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
Total: 1
* 📝 `PuppetPool`



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

- **Comment-to-Source Ratio:** On average there are`23.43` code lines per comment (lower=better).
- **ToDo's:** `0` 

#### <span id=t-components>Components</span>

| 📝Contracts   | 📚Libraries | 🔍Interfaces | 🎨Abstract |
| ------------- | ----------- | ------------ | ---------- |
| 1 | 0  | 2  | 0 |

#### <span id=t-exposed-functions>Exposed Functions</span>

This section lists functions that are explicitly declared public or payable. Please note that getter methods for public stateVars are not included.  

| 🌐Public   | 💰Payable |
| ---------- | --------- |
| 42 | 2  | 

| External   | Internal | Private | Pure | View |
| ---------- | -------- | ------- | ---- | ---- |
| 41 | 38  | 1 | 0 | 4 |

#### <span id=t-statevariables>StateVariables</span>

| Total      | 🌐Public  |
| ---------- | --------- |
| 4  | 4 |

#### <span id=t-capabilities>Capabilities</span>

| Solidity Versions observed | 🧪 Experimental Features | 💰 Can Receive Funds | 🖥 Uses Assembly | 💣 Has Destroyable Contracts | 
| -------------------------- | ------------------------ | -------------------- | ---------------- | ---------------------------- |
| `=0.8.25` |  | `yes` | **** | **** | 

| 📤 Transfers ETH | ⚡ Low-Level Calls | 👥 DelegateCall | 🧮 Uses Hash Functions | 🔖 ECRecover | 🌀 New/Create/Create2 |
| ---------------- | ----------------- | --------------- | ---------------------- | ------------ | --------------------- |
| `yes` | **** | **** | **** | **** | **** | 

| ♻️ TryCatch | Σ Unchecked |
| ---------- | ----------- |
| **** | `yes` |

#### <span id=t-package-imports>Dependencies / External Imports</span>

| Dependency / Import Path | Count  | 
| ------------------------ | ------ |
| @openzeppelin/contracts/utils/Address.sol | 1 |
| @openzeppelin/contracts/utils/ReentrancyGuard.sol | 1 |

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
| src/puppet/PuppetPool.sol | ae8bd441a3db7d4b046f3e24de0126b5530b1663 |
| src/puppet/IUniswapV1Factory.sol | 2ba1dfeeda10f50a2255bb956910a592d20943bc |
| src/puppet/IUniswapV1Exchange.sol | 4fa930b93b79d6b94320f29af7e854f31da1b367 |


 Contracts Description Table


|  Contract  |         Type        |       Bases      |                  |                 |
|:----------:|:-------------------:|:----------------:|:----------------:|:---------------:|
|     └      |  **Function Name**  |  **Visibility**  |  **Mutability**  |  **Modifiers**  |
||||||
| **PuppetPool** | Implementation | ReentrancyGuard |||
| └ | <Constructor> | Public ❗️ | 🛑  |NO❗️ |
| └ | borrow | External ❗️ |  💵 | nonReentrant |
| └ | calculateDepositRequired | Public ❗️ |   |NO❗️ |
| └ | _computeOraclePrice | Private 🔐 |   | |
||||||
| **IUniswapV1Factory** | Interface |  |||
| └ | createExchange | External ❗️ | 🛑  |NO❗️ |
| └ | exchangeTemplate | External ❗️ |   |NO❗️ |
| └ | getExchange | External ❗️ |   |NO❗️ |
| └ | getToken | External ❗️ | 🛑  |NO❗️ |
| └ | getTokenWithId | External ❗️ | 🛑  |NO❗️ |
| └ | initializeFactory | External ❗️ | 🛑  |NO❗️ |
||||||
| **IUniswapV1Exchange** | Interface |  |||
| └ | addLiquidity | External ❗️ |  💵 |NO❗️ |
| └ | allowance | External ❗️ | 🛑  |NO❗️ |
| └ | approve | External ❗️ | 🛑  |NO❗️ |
| └ | balanceOf | External ❗️ | 🛑  |NO❗️ |
| └ | decimals | External ❗️ | 🛑  |NO❗️ |
| └ | ethToTokenSwapInput | External ❗️ | 🛑  |NO❗️ |
| └ | ethToTokenSwapOutput | External ❗️ | 🛑  |NO❗️ |
| └ | ethToTokenTransferInput | External ❗️ | 🛑  |NO❗️ |
| └ | ethToTokenTransferOutput | External ❗️ | 🛑  |NO❗️ |
| └ | factoryAddress | External ❗️ | 🛑  |NO❗️ |
| └ | getEthToTokenInputPrice | External ❗️ | 🛑  |NO❗️ |
| └ | getEthToTokenOutputPrice | External ❗️ | 🛑  |NO❗️ |
| └ | getTokenToEthInputPrice | External ❗️ | 🛑  |NO❗️ |
| └ | getTokenToEthOutputPrice | External ❗️ | 🛑  |NO❗️ |
| └ | name | External ❗️ | 🛑  |NO❗️ |
| └ | removeLiquidity | External ❗️ | 🛑  |NO❗️ |
| └ | setup | External ❗️ | 🛑  |NO❗️ |
| └ | symbol | External ❗️ | 🛑  |NO❗️ |
| └ | tokenAddress | External ❗️ | 🛑  |NO❗️ |
| └ | tokenToEthSwapInput | External ❗️ | 🛑  |NO❗️ |
| └ | tokenToEthSwapOutput | External ❗️ | 🛑  |NO❗️ |
| └ | tokenToEthTransferInput | External ❗️ | 🛑  |NO❗️ |
| └ | tokenToEthTransferOutput | External ❗️ | 🛑  |NO❗️ |
| └ | tokenToExchangeSwapInput | External ❗️ | 🛑  |NO❗️ |
| └ | tokenToExchangeSwapOutput | External ❗️ | 🛑  |NO❗️ |
| └ | tokenToExchangeTransferInput | External ❗️ | 🛑  |NO❗️ |
| └ | tokenToExchangeTransferOutput | External ❗️ | 🛑  |NO❗️ |
| └ | tokenToTokenSwapInput | External ❗️ | 🛑  |NO❗️ |
| └ | tokenToTokenSwapOutput | External ❗️ | 🛑  |NO❗️ |
| └ | tokenToTokenTransferInput | External ❗️ | 🛑  |NO❗️ |
| └ | tokenToTokenTransferOutput | External ❗️ | 🛑  |NO❗️ |
| └ | totalSupply | External ❗️ | 🛑  |NO❗️ |
| └ | transfer | External ❗️ | 🛑  |NO❗️ |
| └ | transferFrom | External ❗️ | 🛑  |NO❗️ |


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


