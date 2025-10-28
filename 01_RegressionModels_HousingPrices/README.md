# **Linear Regression for Housing Prices Prediction**

[Project Ongoing. Will be updated momentarily...]

---

**Objective:**

* Predict housing prices based on variables describing different aspect of the houses.

* Choose the variables with the highest predictive value among the 79 explanatory variables the describe the houses.

* Train and optimize a regression model that can predict housing prices with the highest predictive accuracy.

* eventually, apply advanced models and make predictions on unseen data.

**Dataset:**

The dataset used in this project is the Ames Housing dataset which was compiled by Dean De Cock. The version used here is downloaded from the [Kaggle House Prices - Advanced Regression](https://www.kaggle.com/competitions/house-prices-advanced-regression-techniques/overview) competition page.


## Notebooks Overview

### 01_Project_Initiation_DataCleaning.ipynb
**Goal:** Clean the dataset and remove variables with low predictive value. Prepare it for analysis and modeling.  
**Files used:**  
- Input: `train.csv`, `data_description.txt`  
- Output: `housing_train_cleaned.csv`

---

### 02_EDA_and_BaselineRegression.ipynb
**Goal:** Explore the cleaned dataset, check correlations, encode categorical features, and train a baseline Linear Regression model.  
**Files used:**  
- Input: `housing_train_cleaned.csv`  
- Output: `pipelines.joblib`, `preprocessors.joblib`

**Highlights:**  
- Established a baseline regression model and tested log-transformed target variable for improved normality.  
- Observed strong performance improvements after log-scaling.

---

### 03_FeatureEngineering_and_LinearModelOptimization.ipynb
**Goal:** Test regression assumptions, create new engineered features, and further optimize the linear model.  
**Files used:**  
- Input: `housing_train_cleaned.csv`, `pipelines.joblib`, `preprocessors.joblib`  
- Output: `housing_train_featured.csv`, `linear_model_pipeline.joblib`

**Highlights:**  
- Added engineered features such as total square footage, house age, total bathrooms, and binary indicators (`HasGarage`, `HasFireplace`).  
- Model performance improved significantly after these steps.

---

### 04_EnsembleModels_and_HyperparameterTuning.ipynb *(under construction)*
**Planned goals:**  
- Train and compare ensemble models (Random Forest, Gradient Boosting, HistGradientBoosting).  
- Use GridSearchCV for hyperparameter tuning.  
- Identify top predictors of `SalePrice`.  
**Files to be used:**  
- Input: `housing_train_featured.csv`, `linear_model_pipeline.joblib`  
- Output: `best_model_pipeline.joblib`

---

### 05_ModelEvaluation_and_TestPredictions.ipynb *(under construction)*
**Planned goals:**  
- Use the best-performing model to generate predictions on unseen data (`test.csv`).  
- Evaluate final performance and prepare submission-ready results.  
**Files to be used:**  
- Input: `test.csv`, `best_model_pipeline.joblib`  
- Output: `predictions.csv`

---

## Results Summary

| Model / Stage                      | R² Score | MAE        | MSE            | RMSE       |
|-----------------------------------|----------:|------------:|----------------:|------------:|
| Baseline Linear Regression        | 0.8590    | 19,871.62   | 1,081,299,320.06 | 32,883.12  |
| Log-Scaled Regression             | 0.9061    | 16,833.96   | 682,604,203.85  | 26,126.70  |
| After Feature Engineering         | 0.9245    | 16,232.36   | 579,303,802.40  | 24,068.73  |
| Ensemble Models & Hyperparameter Tuning | *Coming* | *Coming* | *Coming* | *Coming* |

---

Next up: testing ensemble models and fine tuning to see how far we can push model performance
```

