# VIX and CEE Equity Return Predictability

Does global investor fear, as measured by the CBOE VIX,
predict next-day returns in Central European stock markets?

This project tests the predictive power of VIX levels and
daily VIX shocks for returns in the WIG20 (Poland), BUX
(Hungary), PX (Czech Republic), and ATX (Austria) over
2018 to 2024, using OLS regression with Newey-West standard
errors, rolling 12-month coefficient analysis, and
high/low VIX regime decomposition.

## Paper
Submitted to ŠVOČ 2026, Faculty of Management,
Comenius University Bratislava, section: Economics and Finance.

## Reproducing the results
1. Clone the repo
2. Create and activate a virtual environment
3. Install dependencies: `pip install -r requirements.txt`
4. Run notebooks in order: 01 through 05

## Structure
- `notebooks/` -> full analysis pipeline
- `src/`       -> reusable helper functions
- `figures/`   -> generated plots (not tracked in git)
- `data/`      -> processed data files (not tracked in git)
- `paper/`     -> final paper and presentation slides
