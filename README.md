
# Telco Customer Churn Prediction 📉

## 🧩 Project Overview
This project analyzes the Telco Customer Churn dataset from Kaggle to identify factors influencing customer churn and to build predictive models to help the business retain customers.

## 🎯 Objective
To predict whether a customer will churn based on demographic, account, and service-related features.

---

In my experience as a senior customer service representative (CSR) for a major telco company, reducing churn is the major agenda at each goal setting team-meeting, week after week, month after month. 


Being an industry that is equally very sensitive to customer churn and employee turnover, telcos cannot rely solely only on CSR's to drive retention. There must be a clear understanding of what drive customers to cancel their plans and move to another service provider so that proper measures can be put into place to combat churn. 


This project aims to identify key reasons for customer churn based on account characteristics by using machine learning to identify future patterns and present actionable insight to the operations team.



## 🗂️ Dataset
- **Source:** [Kaggle - Telco Customer Churn](https://www.kaggle.com/blastchar/telco-customer-churn)
- **Rows:** 7,043
- **Features:** 21 (both categorical and numerical)
- **Target:** `Churn` (Yes / No)

## ⚙️ Steps Performed
1. **Data Cleaning** – handled missing values, encoded categorical features  
2. **Exploratory Data Analysis (EDA)** – churn rate visualization, feature correlations  
3. **Modeling** – Logistic Regression, Random Forest, XGBoost  
4. **Evaluation** – compared models using accuracy, F1-score, ROC-AUC  
5. **Insights** – identified high-risk churn segments  

## 📈 Results
| Model | ROC-AUC | Accuracy |
|--------|----------|-----------|
| Logistic Regression | 0.81 | 80% |
| Random Forest | 0.84 | 82% |
| -- | **--** | **83%** |

> Top churn drivers: short tenure, high monthly charges, and month-to-month contracts.

## 💡 Business Recommendations
- xxxx xxxxx xxxxx
- xxxx xxxxx xxxxx
- xxxx xxxxx xxxxx  

## 🧰 Tech Stack
- Python (Pandas, NumPy, Scikit-learn, XGBoost)
- Matplotlib, Seaborn for EDA
- Google Colab for experimentation
- GitHub for version control

## 📁 Project Structure
under construction
