# 🛠️  Opening-Range Breakout (ORB) Trading Bot

*Initial commit  ·  14 July 2025*

This repo documents my end-to-end build of an intraday ORB
strategy, from data loading to realistic back-testing with fees,
slippage and FX costs.

| Module | Highlights |
|--------|------------|
| **Data loader** | 5 yrs of 1-min Apple (AAPL) bars via Alpaca Market API. |
| **Strategy core** | Configurable hyperparameters including opening window, stop-loss/target sizing. |
| **Cost model** | IBKR tiered commission, venue taker fees, NSCC / TAF / SEC levies, 0.01 % slippage, AutoFX ±0.03 %. |
| **Back-tester** | minute-loop engine with GBP account, USD settlement, daily mark-to-market. |

### Current results (AAPL 2020-2025, £10,000 start)

| Metric             | Gross (no costs) | Net (all costs) |
|--------------------|------------------|-----------------|
| **Sharpe**         | **1.63**         | **-1.04**       |
| **Total return**   | 110 %            | –38 %           |
| **Trades**         | 973              | 980             |

> **Observation:** commission + AutoFX dominate P&L at small
> capital. At £100,000 the same rules yield net Sharpe ≈ **–0.29**
> (still negative but less corrosive).

To run backtesting, you need to register for Alpaca Market API to obtain data. (Data is free to use upon registration. )

Live trading: I'm assuming IBKR TWS API (hence the cost model) for obtaining live data once strategy is ready for paper trading or production.

---

*Everything here is research-only, not investment advice.*
