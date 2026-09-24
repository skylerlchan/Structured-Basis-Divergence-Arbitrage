# Structured Basis Divergence Arbitrage

Backtest of a delta-neutral BTC funding strategy: short BTC perpetual futures, where funding
is structurally biased positive, against long BTC exposure financed with ETH spot collateral.
The strategy earns the funding yield with minimal directional exposure and rebalances on
volatility-aware thresholds instead of continuous optimization.

- Rebalance the short BTC perp when BTCUSD moves 30% from the last trigger
- Reallocate ETH collateral when ETHBTC falls 30% from the last trigger
- All costs modeled: BTC borrow at 1% APR, 0.28% perp fee, 0.20% spot fee, slippage

Backtest window: Jan 2020 to mid 2025, Binance funding history. The performance table is in
`SABS.pdf` and is reproduced by the notebook.

Related publication: [Leveraged BTC Funding Carry Algorithm](https://doi.org/10.2139/ssrn.5292305)
(SSRN, 2025), a sole-author paper on the delta-neutral long-spot / short-perpetual version of
this idea with dynamic hedge resizing and reinvested 8-hour funding.

## Files

| File | What it is |
|---|---|
| `Structured_Basis_Divergence_Arbitrage.ipynb` | The full backtest, from merged data to equity curve |
| `SABS.pdf` | Strategy summary: thesis, rules, assumptions, performance table |
| `merged_funding_price_data.csv` | Input: funding rates and prices, aligned |
| `equity_curve_final.csv` | Output: equity curve |
| `rebalancing_log_final.csv` | Output: every rebalance trigger |
| `equity_curve_with_rebalances.png`, `strategy_performance_summary.png` | Charts |

## Run

```bash
pip install pandas numpy matplotlib jupyter
jupyter notebook Structured_Basis_Divergence_Arbitrage.ipynb
```
