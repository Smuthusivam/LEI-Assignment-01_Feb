# LEI Assignment 01 — Solar Irradiance Forecasting

A complete machine learning pipeline for solar irradiance (GHI) forecasting using NSRDB 2022 data from a location in Spain.

## Project Structure

```
LEI-Assignment-01_Feb/
├── Data/
│   └── solar2022.csv               # Raw NSRDB hourly solar data (2022)
├── Outputs/
│   ├── df_engineered.csv           # Feature-engineered dataset (48 features)
│   ├── correlation_with_ghi.png    # Feature correlation with GHI
│   ├── correlation_heatmap_engineered.png
│   ├── acf_pacf.png                # Autocorrelation analysis
│   └── forecast_final.png          # Final model comparison plot
├── Tasks/
│   ├── Tasks_1/                    # Task 1: Exploratory Data Analysis
│   │   ├── Data Analysis.ipynb
│   │   └── README.md
│   └── Tasks_2/                    # Task 2: Feature Engineering & ML Models
│       ├── solar_feature_engineering.ipynb
│       ├── Machine Learning Models.ipynb
│       └── README.md
└── README.md
```

## Dataset

| Property | Value |
|----------|-------|
| Source | NSRDB (National Solar Radiation Database) |
| Location | Lat 40.97°N, Lon -4.54°W, Elevation 895m (Spain) |
| Time Period | Full year 2022 |
| Frequency | 30-minute intervals |
| Total Records | 8,760 rows × 25 columns |
| Target Variable | GHI (Global Horizontal Irradiance, W/m²) |

## Tasks Overview

### Task 1 — Exploratory Data Analysis
- Data loading, cleaning, and timestamp construction
- Statistical summaries and feature descriptions
- Correlation analysis and seasonal pattern discovery
- Normalization techniques (Min-Max, Z-score)
- Time-series stationarity testing (ADF), ACF/PACF analysis

### Task 2 — Feature Engineering & Forecasting
- 48 engineered features: solar geometry, temporal, lag, rolling statistics, interactions
- Three forecasting models: ARIMA, SARIMA, SARIMAX
- Best model: **SARIMAX(5,0,1)(1,1,1,24)** — RMSE: **90.96 W/m²**

## Key Results

| Model | RMSE (W/m²) | MAE (W/m²) |
|-------|-------------|------------|
| ARIMA(2,0,2) | 194.99 | 185.62 |
| SARIMA(2,0,2)(1,0,1,24) | 155.99 | 86.22 |
| SARIMAX(5,0,1)(1,1,1,24) | **90.96** | **44.22** |
