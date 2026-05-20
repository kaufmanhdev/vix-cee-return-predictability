# Does Investor Fear Travel?

**VIX Spillovers and Equity Return Predictability in Central European Markets**

Empirical research on whether the CBOE Volatility Index (VIX) predicts next-day equity returns in four Central European markets. Presented at ŠVOČ 2026, Faculty of Management, Comenius University in Bratislava.

---

## The question

When US investor fear spikes, Central European markets fall the next morning. That contemporaneous co-movement is well documented. This project asks a sharper, asymmetric question:

> Does the VIX, observed at the close of the US session on day *t*, **predict** next-day returns in Central European markets on day *t+1*, after those markets have already opened at prices reflecting the prior US session?

The four markets studied are the **WIG20** (Poland), **BUX** (Hungary), **PX** (Czech Republic), and **ATX** (Austria), using daily data from January 2018 to December 2024 (1,637 aligned trading days).

## Key findings

- **VIX changes negatively predict next-day CEE returns** in all four markets. The VIX *level* carries no predictive content; the predictive information is in the daily *change*.
- **The relationship is remarkably persistent.** Across 1,384 rolling 252-day windows, the coefficient is negative in 97–99% of windows in every market.
- **Predictability is 2–3× stronger in calm markets than in crises**, which inverts the standard contagion-amplification view. This is the central and most counterintuitive result.
- **In the pre-COVID subperiod, the VIX alone explained ~9.4% of next-day variance in the Czech PX**, exceptionally high for daily-frequency return predictability.
- Results strengthen to 1% significance in all four markets after GARCH(1,1) standardization, confirming the effect operates on the conditional mean of returns rather than on their variance.

## Methodology

Five complementary specifications, each addressing a different concern:

| Specification | Purpose |
|---|---|
| Baseline OLS with Newey-West HAC standard errors | Core predictive regression, robust to heteroskedasticity and serial correlation |
| Rolling 252-day window estimation | Temporal stability of the coefficient |
| Regime interaction (VIX > 25 threshold) | Whether predictability strengthens or weakens in crises |
| GARCH(1,1) standardization | Robustness to conditional heteroskedasticity |
| Pre/post-COVID subperiod split | Stability across structurally distinct regimes |

## Repository structure

```
notebooks/
  01_data_collection.ipynb     Data download, alignment, log returns, volatility proxies
  02_diagnostics.ipynb         Descriptive stats, ADF stationarity tests, correlations
  03_ols_regression.ipynb      Baseline OLS with Newey-West HAC standard errors
  04_rolling_window.ipynb      Rolling 252-day window estimation
  05_regime_analysis.ipynb     Crisis/calm interaction regressions
  06_garch_robustness.ipynb    GARCH(1,1) fitting and standardized re-estimation
  07_subperiod_analysis.ipynb  Pre/post-COVID subperiod regressions
data/                          Daily price data (.parquet)
figures/                       Generated charts
```

## Data sources

- **VIX**: CBOE, via Yahoo Finance
- **WIG20, BUX, PX**: Stooq
- **ATX**: Wiener Börse historical archive

## Reproducing the results

```bash
git clone https://github.com/clonedfoxx/vix-cee-return-predictability.git
cd vix-cee-return-predictability
pip install -r requirements.txt
jupyter lab
```

Run the notebooks in order, 01 through 07. Each writes its outputs to `data/` and `figures/` for the next stage. Requires Python 3.11+.

**Core dependencies:** pandas, numpy, statsmodels, arch, scipy, matplotlib, seaborn, pyarrow.

## Tech stack

Python · pandas · NumPy · statsmodels · arch · SciPy · matplotlib · seaborn

## License

MIT. See [LICENSE](LICENSE).

## Author

Herman Kaufman, Faculty of Management, Comenius University in Bratislava.

The full paper is available in the repository. This work was reviewed and presented at ŠVOČ 2026 (Section: Economics and Finance).
