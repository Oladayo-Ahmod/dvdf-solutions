
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
| 🔍 | src/curvy-puppet/IStableSwap.sol | **** | 1 | 70 | 27 | 23 | 2 | 85 | **<abbr title='Payable Functions'>💰</abbr>** |
| 🔍 | src/curvy-puppet/ICryptoSwapPool.sol | **** | 1 | 166 | 48 | 39 | 6 | 155 | **<abbr title='Payable Functions'>💰</abbr>** |
| 🔍 | src/curvy-puppet/ICryptoSwapFactory.sol | **** | 1 | 71 | 32 | 24 | 6 | 51 | **** |
| 📝 | src/curvy-puppet/CurvyPuppetOracle.sol | 1 | **** | 38 | 38 | 27 | 2 | 19 | **** |
| 📝 | src/curvy-puppet/CurvyPuppetLending.sol | 1 | **** | 136 | 136 | 100 | 6 | 80 | **<abbr title='Initiates ETH Value Transfer'>📤</abbr>** |
| 📝🔍 | **Totals** | **2** | **3** | **481**  | **281** | **213** | **22** | **390** | **<abbr title='Payable Functions'>💰</abbr><abbr title='Initiates ETH Value Transfer'>📤</abbr>** |

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
* 📝 `CurvyPuppetOracle`
* 📝 `CurvyPuppetLending`



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

- **Comment-to-Source Ratio:** On average there are`18.77` code lines per comment (lower=better).
- **ToDo's:** `0` 

#### <span id=t-components>Components</span>

| 📝Contracts   | 📚Libraries | 🔍Interfaces | 🎨Abstract |
| ------------- | ----------- | ------------ | ---------- |
| 2 | 0  | 3  | 0 |

#### <span id=t-exposed-functions>Exposed Functions</span>

This section lists functions that are explicitly declared public or payable. Please note that getter methods for public stateVars are not included.  

| 🌐Public   | 💰Payable |
| ---------- | --------- |
| 137 | 12  | 

| External   | Internal | Private | Pure | View |
| ---------- | -------- | ------- | ---- | ---- |
| 135 | 45  | 2 | 0 | 84 |

#### <span id=t-statevariables>StateVariables</span>

| Total      | 🌐Public  |
| ---------- | --------- |
| 7  | 7 |

#### <span id=t-capabilities>Capabilities</span>

| Solidity Versions observed | 🧪 Experimental Features | 💰 Can Receive Funds | 🖥 Uses Assembly | 💣 Has Destroyable Contracts | 
| -------------------------- | ------------------------ | -------------------- | ---------------- | ---------------------------- |
| `=0.8.25` |  | `yes` | **** | **** | 

| 📤 Transfers ETH | ⚡ Low-Level Calls | 👥 DelegateCall | 🧮 Uses Hash Functions | 🔖 ECRecover | 🌀 New/Create/Create2 |
| ---------------- | ----------------- | --------------- | ---------------------- | ------------ | --------------------- |
| `yes` | **** | **** | **** | **** | **** | 

| ♻️ TryCatch | Σ Unchecked |
| ---------- | ----------- |
| **** | **** |

#### <span id=t-package-imports>Dependencies / External Imports</span>

| Dependency / Import Path | Count  | 
| ------------------------ | ------ |
| @openzeppelin/contracts/interfaces/IERC20.sol | 1 |
| @openzeppelin/contracts/utils/ReentrancyGuard.sol | 1 |
| @openzeppelin/contracts/utils/math/SafeCast.sol | 1 |
| forge-std/console.sol | 1 |
| permit2/interfaces/IPermit2.sol | 1 |
| solady/auth/Ownable.sol | 1 |
| solmate/utils/FixedPointMathLib.sol | 1 |

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
| src/curvy-puppet/IStableSwap.sol | c5473ea0d0b207ad82638c884d30720173c6e3c7 |
| src/curvy-puppet/ICryptoSwapPool.sol | 6f2b9fb451d2cfaf6e4724a8374331cfb889fba1 |
| src/curvy-puppet/ICryptoSwapFactory.sol | 8e116a7b5ff9a78f902571fc6de016f39cc8b776 |
| src/curvy-puppet/CurvyPuppetOracle.sol | 8d8140d9f4d0633bf0f3f52758508245efa87318 |
| src/curvy-puppet/CurvyPuppetLending.sol | 7af812683c5e81c0d64e268d9240408564805c09 |


 Contracts Description Table


|  Contract  |         Type        |       Bases      |                  |                 |
|:----------:|:-------------------:|:----------------:|:----------------:|:---------------:|
|     └      |  **Function Name**  |  **Visibility**  |  **Mutability**  |  **Modifiers**  |
||||||
| **IStableSwap** | Interface |  |||
| └ | A | External ❗️ |   |NO❗️ |
| └ | A_precise | External ❗️ |   |NO❗️ |
| └ | add_liquidity | External ❗️ |  💵 |NO❗️ |
| └ | admin_actions_deadline | External ❗️ |   |NO❗️ |
| └ | admin_balances | External ❗️ |   |NO❗️ |
| └ | admin_fee | External ❗️ |   |NO❗️ |
| └ | apply_new_fee | External ❗️ | 🛑  |NO❗️ |
| └ | apply_transfer_ownership | External ❗️ | 🛑  |NO❗️ |
| └ | balances | External ❗️ |   |NO❗️ |
| └ | calc_token_amount | External ❗️ |   |NO❗️ |
| └ | calc_withdraw_one_coin | External ❗️ |   |NO❗️ |
| └ | coins | External ❗️ |   |NO❗️ |
| └ | commit_new_fee | External ❗️ | 🛑  |NO❗️ |
| └ | commit_transfer_ownership | External ❗️ | 🛑  |NO❗️ |
| └ | donate_admin_fees | External ❗️ | 🛑  |NO❗️ |
| └ | exchange | External ❗️ |  💵 |NO❗️ |
| └ | fee | External ❗️ |   |NO❗️ |
| └ | future_A | External ❗️ |   |NO❗️ |
| └ | future_A_time | External ❗️ |   |NO❗️ |
| └ | future_admin_fee | External ❗️ |   |NO❗️ |
| └ | future_fee | External ❗️ |   |NO❗️ |
| └ | future_owner | External ❗️ |   |NO❗️ |
| └ | get_dy | External ❗️ |   |NO❗️ |
| └ | get_virtual_price | External ❗️ |   |NO❗️ |
| └ | initial_A | External ❗️ |   |NO❗️ |
| └ | initial_A_time | External ❗️ |   |NO❗️ |
| └ | kill_me | External ❗️ | 🛑  |NO❗️ |
| └ | lp_token | External ❗️ |   |NO❗️ |
| └ | owner | External ❗️ |   |NO❗️ |
| └ | ramp_A | External ❗️ | 🛑  |NO❗️ |
| └ | remove_liquidity | External ❗️ | 🛑  |NO❗️ |
| └ | remove_liquidity_imbalance | External ❗️ | 🛑  |NO❗️ |
| └ | remove_liquidity_one_coin | External ❗️ | 🛑  |NO❗️ |
| └ | revert_new_parameters | External ❗️ | 🛑  |NO❗️ |
| └ | revert_transfer_ownership | External ❗️ | 🛑  |NO❗️ |
| └ | stop_ramp_A | External ❗️ | 🛑  |NO❗️ |
| └ | transfer_ownership_deadline | External ❗️ |   |NO❗️ |
| └ | unkill_me | External ❗️ | 🛑  |NO❗️ |
| └ | withdraw_admin_fees | External ❗️ | 🛑  |NO❗️ |
||||||
| **ICryptoSwapPool** | Interface |  |||
| └ | <Fallback> | External ❗️ |  💵 |NO❗️ |
| └ | A | External ❗️ |   |NO❗️ |
| └ | D | External ❗️ |   |NO❗️ |
| └ | add_liquidity | External ❗️ |  💵 |NO❗️ |
| └ | add_liquidity | External ❗️ |  💵 |NO❗️ |
| └ | add_liquidity | External ❗️ |  💵 |NO❗️ |
| └ | adjustment_step | External ❗️ |   |NO❗️ |
| └ | admin_actions_deadline | External ❗️ |   |NO❗️ |
| └ | admin_fee | External ❗️ |   |NO❗️ |
| └ | allowed_extra_profit | External ❗️ |   |NO❗️ |
| └ | apply_new_parameters | External ❗️ | 🛑  |NO❗️ |
| └ | balances | External ❗️ |   |NO❗️ |
| └ | calc_token_amount | External ❗️ |   |NO❗️ |
| └ | calc_withdraw_one_coin | External ❗️ |   |NO❗️ |
| └ | claim_admin_fees | External ❗️ | 🛑  |NO❗️ |
| └ | coins | External ❗️ |   |NO❗️ |
| └ | commit_new_parameters | External ❗️ | 🛑  |NO❗️ |
| └ | exchange | External ❗️ |  💵 |NO❗️ |
| └ | exchange | External ❗️ |  💵 |NO❗️ |
| └ | exchange | External ❗️ |  💵 |NO❗️ |
| └ | exchange_extended | External ❗️ |  💵 |NO❗️ |
| └ | exchange_underlying | External ❗️ |  💵 |NO❗️ |
| └ | exchange_underlying | External ❗️ |  💵 |NO❗️ |
| └ | factory | External ❗️ |   |NO❗️ |
| └ | fee | External ❗️ |   |NO❗️ |
| └ | fee_gamma | External ❗️ |   |NO❗️ |
| └ | future_A_gamma | External ❗️ |   |NO❗️ |
| └ | future_A_gamma_time | External ❗️ |   |NO❗️ |
| └ | future_adjustment_step | External ❗️ |   |NO❗️ |
| └ | future_admin_fee | External ❗️ |   |NO❗️ |
| └ | future_allowed_extra_profit | External ❗️ |   |NO❗️ |
| └ | future_fee_gamma | External ❗️ |   |NO❗️ |
| └ | future_ma_half_time | External ❗️ |   |NO❗️ |
| └ | future_mid_fee | External ❗️ |   |NO❗️ |
| └ | future_out_fee | External ❗️ |   |NO❗️ |
| └ | gamma | External ❗️ |   |NO❗️ |
| └ | get_dy | External ❗️ |   |NO❗️ |
| └ | get_virtual_price | External ❗️ |   |NO❗️ |
| └ | initial_A_gamma | External ❗️ |   |NO❗️ |
| └ | initial_A_gamma_time | External ❗️ |   |NO❗️ |
| └ | initialize | External ❗️ | 🛑  |NO❗️ |
| └ | last_prices | External ❗️ |   |NO❗️ |
| └ | last_prices_timestamp | External ❗️ |   |NO❗️ |
| └ | lp_price | External ❗️ |   |NO❗️ |
| └ | ma_half_time | External ❗️ |   |NO❗️ |
| └ | mid_fee | External ❗️ |   |NO❗️ |
| └ | out_fee | External ❗️ |   |NO❗️ |
| └ | price_oracle | External ❗️ |   |NO❗️ |
| └ | price_scale | External ❗️ |   |NO❗️ |
| └ | ramp_A_gamma | External ❗️ | 🛑  |NO❗️ |
| └ | remove_liquidity | External ❗️ | 🛑  |NO❗️ |
| └ | remove_liquidity | External ❗️ | 🛑  |NO❗️ |
| └ | remove_liquidity | External ❗️ | 🛑  |NO❗️ |
| └ | remove_liquidity_one_coin | External ❗️ | 🛑  |NO❗️ |
| └ | remove_liquidity_one_coin | External ❗️ | 🛑  |NO❗️ |
| └ | remove_liquidity_one_coin | External ❗️ | 🛑  |NO❗️ |
| └ | revert_new_parameters | External ❗️ | 🛑  |NO❗️ |
| └ | stop_ramp_A_gamma | External ❗️ | 🛑  |NO❗️ |
| └ | token | External ❗️ |   |NO❗️ |
| └ | virtual_price | External ❗️ |   |NO❗️ |
| └ | xcp_profit | External ❗️ |   |NO❗️ |
| └ | xcp_profit_a | External ❗️ |   |NO❗️ |
||||||
| **ICryptoSwapFactory** | Interface |  |||
| └ | accept_transfer_ownership | External ❗️ | 🛑  |NO❗️ |
| └ | admin | External ❗️ |   |NO❗️ |
| └ | commit_transfer_ownership | External ❗️ | 🛑  |NO❗️ |
| └ | deploy_gauge | External ❗️ | 🛑  |NO❗️ |
| └ | deploy_pool | External ❗️ | 🛑  |NO❗️ |
| └ | fee_receiver | External ❗️ |   |NO❗️ |
| └ | find_pool_for_coins | External ❗️ |   |NO❗️ |
| └ | find_pool_for_coins | External ❗️ |   |NO❗️ |
| └ | future_admin | External ❗️ |   |NO❗️ |
| └ | gauge_implementation | External ❗️ |   |NO❗️ |
| └ | get_balances | External ❗️ |   |NO❗️ |
| └ | get_coin_indices | External ❗️ |   |NO❗️ |
| └ | get_coins | External ❗️ |   |NO❗️ |
| └ | get_decimals | External ❗️ |   |NO❗️ |
| └ | get_eth_index | External ❗️ |   |NO❗️ |
| └ | get_gauge | External ❗️ |   |NO❗️ |
| └ | get_token | External ❗️ |   |NO❗️ |
| └ | pool_count | External ❗️ |   |NO❗️ |
| └ | pool_implementation | External ❗️ |   |NO❗️ |
| └ | pool_list | External ❗️ |   |NO❗️ |
| └ | set_fee_receiver | External ❗️ | 🛑  |NO❗️ |
| └ | set_gauge_implementation | External ❗️ | 🛑  |NO❗️ |
| └ | set_pool_implementation | External ❗️ | 🛑  |NO❗️ |
| └ | set_token_implementation | External ❗️ | 🛑  |NO❗️ |
| └ | token_implementation | External ❗️ |   |NO❗️ |
||||||
| **CurvyPuppetOracle** | Implementation | Ownable |||
| └ | <Constructor> | Public ❗️ | 🛑  |NO❗️ |
| └ | getPrice | External ❗️ |   |NO❗️ |
| └ | setPrice | External ❗️ | 🛑  | onlyOwner |
||||||
| **CurvyPuppetLending** | Implementation | ReentrancyGuard |||
| └ | <Constructor> | Public ❗️ | 🛑  |NO❗️ |
| └ | deposit | External ❗️ | 🛑  | nonReentrant |
| └ | withdraw | External ❗️ | 🛑  | nonReentrant |
| └ | borrow | External ❗️ | 🛑  |NO❗️ |
| └ | redeem | External ❗️ | 🛑  | nonReentrant |
| └ | liquidate | External ❗️ | 🛑  | nonReentrant |
| └ | getBorrowValue | Public ❗️ |   |NO❗️ |
| └ | getCollateralValue | Public ❗️ |   |NO❗️ |
| └ | getBorrowAmount | External ❗️ |   |NO❗️ |
| └ | getCollateralAmount | External ❗️ |   |NO❗️ |
| └ | _pullAssets | Private 🔐 | 🛑  | |
| └ | _getLPTokenPrice | Private 🔐 |   | |


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


