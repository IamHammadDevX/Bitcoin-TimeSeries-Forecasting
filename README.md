# Semester-Level Time Series Forecasting Project: Bitcoin Prices

## Overview
- End-to-end, professor-ready time-series project using a real-world OHLCV dataset (`Bitcoin.csv`).
- Target variable: `Close`. Notebook implements data preprocessing, extensive EDA, stationarity diagnostics, feature engineering, time-aware train/test split, ARIMA/SARIMA/Auto-ARIMA training, evaluation (MAE, RMSE, MAPE), and best-model persistence.

## Features
- Clean, modular notebook structure suitable for academic evaluation and reuse.
- Robust preprocessing with time-aware interpolation, duplicate removal, outlier handling, optional log transform.
- High-density EDA producing many plots with concise bullet insights per figure.
- Calendar and seasonality analysis: month-of-year, day-of-week, heatmaps, decomposition.
- Stationarity diagnostics: ADF tests and visual comparisons before/after transformations.
- Feature engineering: lag features, rolling statistics, EMAs, volatility proxies.
- Time-aware train/test split (no shuffle) with clear visualization.
- Multiple forecasting baselines and models: Naive, ARIMA, SARIMA, Auto-ARIMA-style grid search.
- Model evaluation using MAE, RMSE, MAPE, with comparative table and best-model selection.
- Model persistence: save best model to `best_model.pkl` and reload verification.
- Practical runtime controls: frequency setting (`asfreq('D')`), warning suppression, tunable grid sizes.
## Files
- `Bitcoin.csv`: dataset with `Date`, `Open`, `High`, `Low`, `Close`, `Volume`.
- `TimeSeries_Forecasting_Project.ipynb`: main notebook with the complete workflow.
- `best_model.pkl`: generated model artifact (ignored by git by default).

## Quickstart (Windows)
- Create a virtual environment:
  - `python -m venv .venv`
  - `.\.venv\Scripts\activate`
- Install dependencies:
  - `pip install pandas numpy matplotlib seaborn statsmodels scikit-learn notebook`
- Launch Jupyter:
  - `jupyter notebook`
- Open and run `TimeSeries_Forecasting_Project.ipynb` top-to-bottom.

## What the Notebook Covers
- Data Loading & Understanding: head/tail/shape/info/describe, time range, inferred frequency, target.
- Preprocessing: datetime index, missing handling (time-aware), duplicates, outlier treatment via winsorized returns, optional log transform, OHLCV resampling.
- EDA: trend, monthly/yearly behavior, day-of-week effects, bull/bear phases, rolling means/EMAs, volatility metrics, seasonal decomposition, seasonal heatmaps, spike/crash detection, cumulative returns, transformations, multivariate relations (Open vs Close, Volume vs Price), correlation and lag analysis.
- Stationarity & Diagnostics: ADF tests on original/log/differenced series, interpretation, visual checks.
- Feature Engineering: lags (1/7/14/30), rolling stats, EMAs, volatility proxy.
- Train–Test Split: 80/20 split, time-aware, visualization.
- Model Training: Naive baseline; ARIMA (AIC-based search near selected `d`); SARIMA (seasonal grid with inferred period); Auto-ARIMA approximation (broader AIC grid using `statsmodels`).
- Evaluation: MAE, RMSE, MAPE with comparison table and best model selection.
- Model Saving: persist best model to `best_model.pkl`, reload example and forecast verification.

## Tips
- Grid searches can be computationally intensive; adjust `p,q,P,Q` ranges or reduce training window for speed.
- Warnings related to inferred frequency and convergence are suppressed for readability; frequency is set via `asfreq('D')` on the daily series.
- Optional: for `pmdarima` true `auto_arima`, install `pip install pmdarima` and integrate if desired.

## Reproducibility
- The workflow is deterministic on fixed data; models use maximum-likelihood estimation which may vary slightly with solver tolerances. For faster consistent runs, constrain search grids.

## License
- No license specified. Add one if you plan to publish.
