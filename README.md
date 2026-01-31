Siap. Ini **README.md** yang **clean, profesional, dan GitHub-ready**, selaras sama isi PPT & workflow lu. Tinggal copy–paste 👇

---

# 🌦️ Weather Forecast & Temperature Prediction in the Philippines (2026)

This project focuses on **weather data analysis and temperature forecasting in the Philippines**, leveraging historical daily weather data from **2020–2023** and machine learning models to generate **forward-looking temperature predictions for 2026**.

The goal is not only to achieve strong predictive performance, but also to ensure **data quality, interpretability, and realistic modeling decisions** based on meteorological and geographical context.

---

## 📌 Project Overview

* **Domain**: Weather & Climate Data Science
* **Location**: Philippines
* **Time Range**: 2020–2023 (historical), 2026 (forecast)
* **Granularity**: Daily data aggregated into regional patterns
* **Regions**: North, Central, South

This project emphasizes:

* Robust **Exploratory Data Analysis (EDA)**
* Careful **outlier validation using real-world references**
* **Time-aware machine learning modeling**
* Avoidance of **data leakage**
* Interpretable and realistic results

---

## 📂 Dataset Description

* **Source**: Philippine cities weather observations
* **Observations**: ~206,000+ daily records
* **Target Variables**:

  * `temperature_2m_min`
  * `temperature_2m_mean`
  * `temperature_2m_max`

### Feature Groups

* **Meteorological**: temperature, wind speed, wind gusts, precipitation
* **Solar-related**: radiation, sunshine duration, evapotranspiration
* **Temporal**: datetime-derived features
* **Spatial**: region-based grouping (North, Central, South)

---

## 🔍 Exploratory Data Analysis (EDA)

Key EDA steps include:

* Distribution analysis (all numerical features are **non-normal / skewed**)
* IQR-based outlier detection (preferred over z-score)
* Correlation analysis (heatmap)
* Seasonal trend visualization (mean, min, max temperature)

### Important Findings

* `precipitation_sum` and `rain_sum` show **perfect correlation (≈1.00)**
  → One feature was dropped to avoid redundancy.
* Temperature trends exhibit **strong seasonal consistency** across years.
* Regional patterns are distinct and meaningful.

---

## 🚨 Outlier Analysis & Data Validation

Outliers were **not blindly removed**.

### Temperature Outliers

* Cold extremes (e.g., Baguio, Malaybalay) align with **highland geography**
* Hot extremes (e.g., Tuguegarao, Cabanatuan) reflect **heat-trap valleys**
* Urban heat effects observed in Metro Manila

✅ Conclusion: Temperature outliers are **physically valid**.

### Wind Anomalies

* Wind speed > **32 m/s**
* Wind gusts > **70 m/s**

Despite real storm events (e.g., Typhoon Goni, Rai), many recorded values exceed **physically plausible surface measurements**.

⚠️ These records were:

* Kept for transparency
* **Excluded from modeling**

---

## ⚙️ Feature Engineering

* **Region grouping** (city → North / Central / South)
* **One-Hot Encoding** for region
* **Cyclical encoding** for month:

  * `month_sin`
  * `month_cos`
* Dropped features causing leakage:

  * Apparent temperature variables
  * Redundant or identifier-only columns

---

## 🧠 Machine Learning Approach

### Train–Test Split (Time-Based)

* **Train**: 2020–2022
* **Test**: 2023

Random splits were avoided to prevent **data leakage**.

### Models Used

* **Decision Tree** (Baseline)
* **Random Forest** (Stable ensemble)
* **XGBoost** (High-performance model)

---

## 📊 Model Performance

### Best Model: **XGBoost (Baseline Configuration)**

* **R²**: ~0.73
* **MAE**: ~0.56 °C
* **RMSE**: ~0.77 °C

Key insight:

* Hyperparameter tuning improved Decision Tree
* Random Forest remained stable
* Over-tuning XGBoost reduced generalization

---

## 🔮 2026 Temperature Forecast Highlights

* **Maximum Temperature**
  🔥 North region peaks at **~34.16°C in May 2026**
* **Mean Temperature**
  Seasonal patterns remain consistent → model captures true seasonality
* **Minimum Temperature**
  Central region shows slightly warmer nights mid-year compared to South

---

## 🛠️ Tech Stack

* Python
* pandas, NumPy
* matplotlib, seaborn
* scikit-learn
* XGBoost
* Random Forest
* Decision Tree

---

## 📈 Key Takeaways

* Weather data requires **domain-aware validation**, not blind cleaning
* Seasonality and region matter more than raw complexity
* Time-aware modeling is critical for realistic forecasting
* Simpler models can outperform over-tuned ones when data is structured well

---

## 👤 Author

**Naufal Dzakia Raiffaza**
Data Analyst / Data Scientist
Interested in weather analytics, time-series modeling, and applied machine learning.

---

## 📬 Feedback & Collaboration

Feel free to open an issue, start a discussion, or reach out if you have:

* Feedback or improvements
* Questions about methodology
* Collaboration ideas

---
