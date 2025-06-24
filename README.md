# 📈 Time Series Sales Forecasting using SARIMA Models (Python)

[![Python](https://img.shields.io/badge/Built%20With-Python-blue?logo=python)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Status](https://img.shields.io/badge/Status-Complete-brightgreen.svg)]()
[![Forecast](https://img.shields.io/badge/Forecast-Ready-orange)]()

---

## 📘 Project Overview

This project implements a **time series forecasting system** in **Python** to predict monthly sales for **three business units (BU1, BU2, BU3)** using **SARIMA models**. Key steps include:

- **Time Series Decomposition**
- **Stationarity Testing (ADF + ACF)**
- **Automated Differencing using `pmdarima.ndiffs()`**
- **Seasonality Confirmation via `diff(12)` and ACF**
- **Model Selection with `auto_arima()`**
- **3-Month Forecasting for Jan–Mar 2018**
- **Model Saving for Deployment**

The dataset includes **35 monthly observations** (Feb 2015 – Dec 2017) across 3 BUs.

---

## 📂 Project Structure

```
.
├── data/
│   ├── raw/
│   │   └── USA FIRM SALES DATA.csv
│   └── processed/
├── models/
│   ├── BU1_sarima_model.pkl
│   ├── BU2_sarima_model.pkl
│   └── BU3_sarima_model.pkl
├── notebooks/
│   └── 01_EDA.ipynb
├── reports/
│   └── figures/
│       └── python_time_series_plots.png
├── src/
│   ├── data_prep.py
│   ├── train_model.py
│   └── utils.py
├── dashboards/
├── environment/
│   ├── environment.yml
│   └── requirements.txt
├── main.py
└── README.md
```

---

## 📊 Model Summary

| BU   | Model                     | SARIMA Order            | Notes             |
|------|---------------------------|--------------------------|-------------------|
| BU1  | SARIMA(0,1,1)(0,1,0)[12] | Seasonal MA(1) Model     | High seasonality  |
| BU2  | SARIMA(1,0,0)(1,1,0)[12] | Seasonal AR(1) Model     | Balanced profile  |
| BU3  | SARIMA(1,0,0)(0,1,0)[12] | Simpler trend-driven     | Stable growth     |

All models were selected using `auto_arima` with seasonality confirmed (`D=1`, `m=12`).

---

## 🔧 Technical Workflow

### Decomposition
- Performed using `seasonal_decompose()`
- Visual inspection of trend, seasonality, and residuals

### Stationarity Testing
- Rolling mean/std and ADF test
- Visual ACF for correlation structure
- Differencing using `pmdarima.ndiffs()`

### Seasonality Detection
- ACF after `.diff(12)` showed lag-12 patterns
- Set `D=1`, `m=12` for all SARIMA models

### Model Training
```python
auto_arima(series,
           seasonal=True,
           m=12,
           D=1,
           stepwise=True,
           suppress_warnings=True)
```

### Forecasting
- Forecasted Jan–Mar 2018 per BU
- Combined forecasts plotted with actual series

---

## 📈 Forecast Results (Jan–Mar 2018)

All 3 BUs forecasted for Q1 2018 using the final SARIMA models.

Forecasts were visualized together, providing stakeholders an overview of expected business performance.

---

## 💾 Model Persistence

Models were saved to disk in:

```
/models/
├── BU1_sarima_model.pkl
├── BU2_sarima_model.pkl
└── BU3_sarima_model.pkl
```

These can be loaded using `joblib.load()` for real-time or scheduled inference.

---

## 📌 Next Steps

- **🌐 Streamlit Dashboard** for real-time forecast exploration
- **📤 API or Batch Forecasting** integration for business use
- **🔁 Model Retraining** as new months of data arrive
- **📊 Evaluation Reports** comparing forecasts to actuals (if available)
- **📦 Deployment Pipeline** using GitHub Actions or Azure

---

## 🎓 Key Learning Outcomes

- How to structure a Python time series project professionally
- The process of decomposition, differencing, stationarity testing
- SARIMA model tuning using `auto_arima`
- Creating production-ready workflows
- Clear visual communication of forecast results

---

## 📬 Contact

Developed by **Business Enterprise Data Architecture (BEDA)**  
📩 Email: [wphiri@beda.ie](mailto:wphiri@beda.ie)  
🔗 LinkedIn: [William Phiri](https://www.linkedin.com/in/william-phiri-866b8443/)  
🧭 _"Get it done the BEDA way"_

---

## 📄 License

This project is licensed under the MIT License. See the LICENSE file for details.
