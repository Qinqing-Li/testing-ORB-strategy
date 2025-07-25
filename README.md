# 🛠️  Opening-Range Breakout (ORB) Trading Bot

*Initial commit  ·  14 July 2025*

<br>

This repository tracks the **full build-out of a Opening-Range Breakout (ORB) bot**. Currently a functional prototype, all classes in classs_sketch.ipynb. 

To run backtesting, you need to register for Alpaca Market API to obtain data. (Data is free to use upon registration. )

<br>

| Module | Highlights |
|--------|------------|
| **Data loader** | 5 yrs of 1-min Apple (AAPL) bars via Alpaca Market API. |
| **Strategy core** | Configurable hyperparameters including opening window, stop-loss/target sizing. |
| **Cost model** | IBKR tiered commission, venue taker fees, NSCC / TAF / SEC levies, 0.01 % slippage, AutoFX ±0.03 %. |
| **Back-tester** | minute-loop engine with GBP account, USD settlement, daily mark-to-market. |
<br>


#### Current results (AAPL 2020-2025, £10,000 start)

| Metric             | Gross (no costs) | Net (all costs) |
|--------------------|------------------|-----------------|
| **Sharpe**         | **1.63**         | **-1.04**       |
| **Total return**   | 110 %            | –38 %           |
| **Trades**         | 973              | 980             |

> commission + AutoFX dominate P&L at small capital, and the size of capital impact the Sharpe. At £100,000 the same rules yield net Sharpe ≈ **–0.29**, at £1,000,000 Sharpe ≈ **1.02**, At £5,000,000 Sharpe ≈ **1.11**. (Purely a thought experiment, impossible to have £1M in UK ISA besides the cost model would be different for larger capital.)

Live trading: I'm assuming IBKR TWS API (hence the cost model) for obtaining live data once strategy is ready for paper trading or production.

<br>

*Everything here is research-only, not investment advice.*
