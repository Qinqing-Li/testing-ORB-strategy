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

---

*Update  ·  3 August 2025*

Testing whether Narrow Range filter (NR7, NR14, NR30) improve the strategy. Short answer: no.  

#### Results (AAPL 2020-2025, £10,000 start, no cost)

| Filter     | Sharpe | Total Return | Trades | Win Rate | Avg Gain/Trade | Profit Factor |
|------------|--------|---------------|--------|-----------|----------------|----------------|
| **None**   | 1.64  | 110.49%     | 973    | 47.03%    | $11.39         | 1.44           |
| **NR7**    | 0.79   | 11.87%        | 155    | 52.90%    | $7.66          | 1.50           |
| **NR14**   | 0.69   | 8.04%         | 90     | 54.44%    | $8.93          | 1.63           |
| **NR30**   | 0.46   | 3.47%         | 43     | 51.16%    | $8.08          | 1.60           |

> Narrow Range filters marginally improve win rate and profit factor, but reduce overall expected returns.

*Everything here is research-only, not investment advice.*
