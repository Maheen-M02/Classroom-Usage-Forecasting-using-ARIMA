# Classroom-Usage-Forecasting-using-ARIMA📊

This project focuses on short-term (next-hour) electricity demand forecasting for indoor spaces such as classrooms or lecture halls.
Using time-series electricity consumption data and optional occupancy-related signals, the system trains a statistical forecasting model (ARIMA / ARIMAX) to predict near-future electricity draw along with confidence intervals.

The primary motivation is to support energy-aware campus management, enabling smarter scheduling, load balancing, and energy optimization.

Problem Statement

Traditional energy monitoring systems provide only historical insights. However, predicting near-term electricity demand—especially when influenced by human occupancy—can enable proactive energy management.

The challenge is to:

Acquire suitable time-indexed electricity and/or occupancy data

Model short-term temporal patterns

Produce interpretable forecasts with uncertainty bounds

Dataset Description

This project uses publicly available time-series datasets suitable for hourly forecasting.

1. Electricity Consumption Data

Source: UCI Machine Learning Repository / Kaggle

Dataset: Individual Household Electric Power Consumption

Resolution: Minute-level (resampled to hourly)

Features:

Global active power

Sub-metered electricity usage

Usage: Acts as a proxy for room or building-level electricity draw

2. (Optional) Occupancy / Sensor Data

Source: UCI Machine Learning Repository

Dataset: Occupancy Detection Dataset

Features:

Environmental sensor readings (CO₂, temperature, humidity, light)

Binary occupancy labels

Usage: Used as an exogenous variable to improve forecasting accuracy (ARIMAX)

Note: Public Wi-Fi MAC log datasets are limited; sensor-based occupancy is a widely accepted academic proxy.

Data Preprocessing

Parse timestamps and set a time-based index

Handle missing values and outliers

Resample electricity data to hourly intervals

Align electricity and occupancy data on a common hourly timeline

Normalize or scale features where required

Modeling Approach
Baseline Model

ARIMA (AutoRegressive Integrated Moving Average)

Trained solely on historical electricity consumption

Extended Model

ARIMAX

Electricity consumption as the target variable

Occupancy indicators as exogenous regressors

Forecast Output

Next-hour electricity demand prediction

95% confidence intervals for uncertainty estimation

Evaluation

Model performance is evaluated using:

Mean Absolute Error (MAE)

Root Mean Squared Error (RMSE)

Visual inspection of forecast vs actual values

Width and calibration of confidence intervals

Visualization & Dashboard

A lightweight dashboard (e.g., Streamlit) presents:

Historical electricity usage

One-step-ahead forecasts

Confidence interval bands

Occupancy trends (if included)

Project Structure
.
├── data/
│   ├── raw/
│   ├── processed/
├── notebooks/
│   ├── exploration.ipynb
│   ├── modeling.ipynb
├── src/
│   ├── preprocess.py
│   ├── train_arima.py
│   ├── forecast.py
├── dashboard/
│   └── app.py
├── README.md
└── requirements.txt

Tools & Technologies

Python

pandas, numpy

statsmodels (ARIMA / ARIMAX)

matplotlib / plotly

Streamlit (dashboard)

Use Cases

Classroom energy optimization

Smart campus infrastructure

Load-aware HVAC and lighting control

Educational demonstration of time-series forecasting

Future Work

Replace proxy data with real Wi-Fi access point logs

Extend forecasting horizon (multi-step forecasts)

Compare ARIMA with LSTM / Prophet models

Integrate real-time streaming data

Disclaimer

The datasets used are public and not tied to a specific classroom.
Results demonstrate methodology and modeling capability, not exact real-world consumption.
