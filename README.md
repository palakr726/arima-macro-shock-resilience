# Forecast Resilience of ARIMA Models Under Macroeconomic Shocks

Mentor-approved undergraduate econometric research testing whether standard
ARIMA models lose forecast accuracy during macroeconomic volatility, and
whether incorporating macroeconomic indicators improves resilience.

## Data
4 FRED time series (retail sales, CPI/inflation, federal funds rate, USD index),
Jan 2019 – Dec 2024, split into stable / volatile / recovery periods
(24 monthly observations each).

## Method
ADF stationarity testing, auto-ARIMA parameter selection, walk-forward
validation. Extended to ARIMAX/VAR incorporating macro indicators.

## Findings
- Baseline MAPE: **4.78% (stable) · 1.02% (volatile) · 0.56% (recovery)**
- The "stable" period was paradoxically the *least* accurate — excluding four
  COVID-crash months dropped its MAPE to **0.85%**, showing the sudden COVID
  shock (not the gradual 2021–22 inflation this study targeted) drove nearly
  all the error. **Shock type mattered more than shock category.**
- An **inflation-only model beat both the baseline and a naive full
  multivariate model in every period** (e.g. volatile: 0.68% vs 1.02% baseline
  vs 2.31% all-variable ARIMAX) — macro-awareness helps, but only when applied
  selectively.
- A fully-specified VAR was **infeasible given limited historical data**
  (`ValueError: maxlags is too large for the number of observations`) —
  itself evidence that model complexity has real limits on small datasets.

## Tools
Python · pandas · statsmodels · pmdarima · Jupyter Notebook
