# 🚲 Bike Sharing — Daily Demand Prediction (RandomForest Regression)

![Python](https://img.shields.io/badge/Python-3.9%2B-blue)
![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-orange)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-lightgrey)
![Status](https://img.shields.io/badge/Status-Completed-success)
![Task](https://img.shields.io/badge/Task-Regression-blueviolet)

---

## 📌 Overview

This project explores a **bike sharing dataset** using machine learning to predict the **daily number of bike rentals (`cnt`)**.

A **RandomForestRegressor** was trained and evaluated, achieving **strong performance (R² ≈ 0.88 on test data)**, providing a solid baseline for demand forecasting.

---

## 🎯 Objective

- Build a regression model to predict daily bike demand  
- Analyze how environmental and calendar factors affect rentals  
- Evaluate model performance and generalization  

---

## 📊 Dataset Description

The dataset contains daily records of bike rentals with features such as:

- 🌤️ **Weather (`weathersit`)**
- 🌡️ **Temperature (`temp`, `atemp`)**
- 💧 **Humidity (`hum`)**
- 🌬️ **Wind speed (`windspeed`)**
- 📅 **Time features (`season`, `mnth`, `weekday`, `workingday`)**
- 👥 **User types (`casual`, `registered`)**
- 🎯 **Target:** `cnt` (total rentals)

---

## ⚙️ Preprocessing

- Removed leakage features:
  - `casual`, `registered`  
  > since: `cnt = casual + registered`

- Dropped unnecessary column:
  - `instant`

- No scaling applied:
  - Tree-based models do not require feature scaling

- No missing values or duplicates detected

---

## 🤖 Model

### RandomForestRegressor

- Used as the main regression model  
- Handles non-linear relationships effectively  
- Robust to noise and feature interactions  

### 🔧 Hyperparameter Tuning

Optimized using **GridSearchCV**:

- `n_estimators`
- `max_depth`
- `min_samples_split`
- `min_samples_leaf`
- `max_features`

---

## 📈 Results

### 🔹 Training Performance
- MAE ≈ **289**
- RMSE ≈ **411**
- R² ≈ **0.954**

### 🔹 Testing Performance
- MAE ≈ **465**
- RMSE ≈ **688**
- R² ≈ **0.877**

---

## 🚨 Key Insight

> The dataset contains **strong structured patterns**, enabling high predictive performance even with a single model.

### Why?

- Demand is driven by:
  - 🌤️ Weather conditions  
  - 🌡️ Temperature  
  - 📅 Working days and seasonality  

👉 The model effectively learns patterns like:

```bash
IF (workingday = 1 AND weather is good AND temperature is moderate)
→ demand increases

ELSE
→ demand decreases
```

---

## 🧠 Interpretation

- The problem is **highly structured**, not random  
- A small set of features dominates predictions:
  - 🌡️ Temperature  
  - 🌤️ Weather  
  - 📅 Working day  

- RandomForest effectively captures **non-linear interactions** between these features  

---

## ⚠️ Important Note

- This is **not severe overfitting**:
  - Test performance remains strong (R² ≈ 0.88)  
  - Only a moderate gap exists between train and test results  
  - The model generalizes reasonably well  

- However:
  - Performance improvements plateau  
  - This suggests **model limitation rather than data limitation**

---

## 📊 What This Project Teaches

- Tree-based models are strong baselines for tabular data  
- Data structure can significantly influence model performance  
- Proper evaluation (train vs test) is essential  
- Avoiding data leakage is critical for valid results  

---

## 🏁 Conclusion

The RandomForest model provides a reliable baseline for predicting bike rental demand, achieving strong performance with minimal preprocessing.

This project highlights the importance of:

- Understanding feature relationships  
- Avoiding data leakage  
- Properly evaluating model generalization  
