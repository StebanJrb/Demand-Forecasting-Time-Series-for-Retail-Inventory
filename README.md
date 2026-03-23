# Demand Forecasting — Time Series for Retail Inventory

## Overview
A multi-method time series forecasting system for retail demand prediction. Compares statistical, decomposition, and ML approaches with systematic experimentation in MLflow. Airflow generates weekly forecasts for operational consumption.

## Architecture
- **Data**: Retail transaction data with seasonality, trends, promotions, and holidays
- **Statistical Baseline**: ARIMA/SARIMAX with automated order selection (auto_arima)
- **Decomposition**: Prophet capturing weekly, monthly, and yearly seasonality plus holiday effects
- **ML Approach**: LightGBM with engineered features — lag values (7, 14, 28 days), rolling statistics (mean, std, min, max), day-of-week/month encoding, promotion flags
- **Evaluation**: MAPE, RMSE, MAE per store-product combination; backtesting with expanding window
- **Serving**: Weekly Airflow DAG writes forecasts to PostgreSQL for operations team

## Tech Stack
- Python 3.11+, Pandas, NumPy
- statsmodels (ARIMA/SARIMAX), Prophet, LightGBM
- MLflow (experiment tracking)
- Apache Airflow 2.x
- PostgreSQL
- Docker & Docker Compose

## What This Demonstrates
- Multiple forecasting methodologies and when to use each
- Time series feature engineering (lags, rolling windows, calendar features)
- Backtesting and walk-forward validation
- MLflow experiment comparison across fundamentally different model types
- Operational forecast delivery via scheduled pipelines

## Status
🚧 In Development

## Project Structure
├── dags/
│   └── weekly_forecast_dag.py
├── src/
│   ├── features/
│   ├── models/
│   │   ├── statistical/
│   │   ├── prophet/
│   │   └── gradient_boost/
│   └── evaluation/
├── notebooks/
├── tests/
├── docker-compose.yml
└── README.md
