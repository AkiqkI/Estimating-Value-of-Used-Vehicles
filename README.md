# 🚗 Rusty Bargain: Estimating Market Value of Used Vehicles

Rusty Bargain, a used car sales service, is developing an app to estimate the market value of vehicles based on historical listings. This project aims to build and compare machine learning models that accurately and efficiently predict the price of a car (in EUR).

## 🎯 Project Objectives

Rusty Bargain is interested in three key aspects:
1. **Prediction quality** — measured by the RMSE metric.
2. **Training time** — total time to fit the model.
3. **Prediction speed** — how fast the model produces outputs.

**Success Criteria:** Achieve a competitive RMSE compared to baseline models while maintaining reasonable training and inference times.

## 🗂️ Data Description

**File:** `car_data.csv`
**Target:** `Price` (EUR)
**Main features:**
`DateCrawled`, `VehicleType`, `RegistrationYear`, `Gearbox`, `Power`, `Model`,
`Mileage`, `RegistrationMonth`, `FuelType`, `Brand`, `NotRepaired`,
`DateCreated`, `NumberOfPictures`, `PostalCode`, `LastSeen`.

## ⚙️ Model Performance Summary

This project involved training and evaluating several regression models. The table below summarizes their performance based on Prediction Quality (RMSE), Training Time, and Prediction Speed. All training and prediction times are **Wall times** (real execution time) measured with the `%%time` magic command.

| **Model**                   | **Hyperparameter Tuning (Wall time)** | **Train (Wall time)** | **Prediction (Wall time)** | **Total Time**            | **RMSE**       | **% RMSE Reduction vs. Baseline** |
|------------------------------|--------------------------------------|-----------------------|-----------------------------|----------------------------|----------------|----------------------------------|
| Linear Regression (Baseline) | -                                    | 8.88 s               | 0.15 s                      | **9.03 s**                | 2747.31582     | -                                |
| Decision Tree Regressor      | 4.08 s                              | 1.97 s               | 0.0595 s                    | **6.11 s**                | 2482.7611      | **9.63%**                        |
| Random Forest Regressor      | 752 s (12 min 32 s)                  | 73 s (1 min 13 s)    | 0.212 s                     | **825.21 s (~13.75 min)** | 1977.73895     | **28.03%**                       |
| LightGBM Regressor           | 0.00000429 s                         | 4.82 s               | 1.75 s                      | **6.57 s**                | 1599.86598     | **41.75%**                       |
| CatBoost Regressor           | 279 s (4 min 39 s)                   | 244 s (4 min 4 s)    | 0.273 s                     | **523.27 s (~8.72 min)**  | 1686.02478     | **38.65%**                       |

*All results are based on consistent train/validation/test splits and the same target variable (`Price` in EUR).*

## 🧾 Conclusions

Throughout this project, we developed and compared multiple regression models to estimate the **market value of used vehicles** based on technical and categorical attributes from **Rusty Bargain’s** dataset. Our goal was to identify a model that balances **accuracy**, **efficiency**, and **scalability** for potential deployment in a pricing application.

The **LightGBM Regressor achieved the lowest RMSE** (1599.87) with a 41.75% reduction compared to baseline, **followed by CatBoost** (1686.02; 38.65%) and Random Forest (1977.74; 28.03%). The Decision Tree showed only moderate improvement (9.63%).

In terms of computation time, **LightGBM proved to be both fast and accurate**, completing the process in about 6.6 seconds. CatBoost also performed well but required longer training time (around 8.7 minutes), while Random Forest was the slowest (about 13.8 minutes).

### 🥇 Best Performing Model

- **LightGBM** achieved the **lowest RMSE (≈1,600 EUR)** with **fast training (≈5 s)** and **low prediction latency (<2 s)**, making it the most efficient and production-ready choice.
- **CatBoost** also performed competitively in terms of quality but required longer training time.

**Final Recommendation:**

**LightGBM proved to be the most balanced and reliable option** for estimating vehicle prices at Rusty Bargain. It combines strong predictive accuracy with fast execution.
