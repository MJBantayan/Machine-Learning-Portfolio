
# Telco Customer Churn Prediction 

## Project Overview
This project analyzes the Telco Customer Churn dataset from Kaggle to identify factors influencing customer churn and to build predictive models to help the business retain customers.

## Objective
To predict whether a customer will churn based on demographic, account, and service-related features.

---

In my experience as a senior customer service representative (CSR) for a major telco company, reducing churn is the major agenda at each goal setting team-meeting, week after week, month after month. 


Being an industry that is equally very sensitive to customer churn and employee turnover, telcos cannot rely solely only on CSR's to drive retention. There must be a clear understanding of what drive customers to cancel their plans and move to another service provider so that proper measures can be put into place to combat churn. 


This project aims to identify key reasons for customer churn based on account characteristics by using machine learning to identify future patterns and present actionable insight to the operations team.



## Dataset
- **Source:** [Kaggle - Telco Customer Churn](https://www.kaggle.com/blastchar/telco-customer-churn)
- **Rows:** 7,043
- **Features:** 21 (both categorical and numerical)
- **Target:** `Churn` (Yes / No)

## Workflow
1. **Data Cleaning** – handled missing values, encoded categorical features  
2. **Exploratory Data Analysis (EDA)** – churn rate visualization, feature correlations, statistical validation  
3. **Modeling** – Logistic Regression, Random Forest, XGBoost  
4. **Evaluation** – compared models using accuracy, F1-score, ROC-AUC  
5. **Insights** – identified high-risk churn segments  

## Model Performance
| Model               |  Accuracy  |   ROC-AUC  |
| :------------------ | :--------: | :--------: |
| Logistic Regression | **0.8031** | **0.8362** |
| Random Forest       |   0.7854   |   0.8217   |
| XGBoost             |   0.7783   |   0.8196   |

Best model: Logistic Regression (highest accuracy and ROC-AUC)

## **Key EDA Findings**

1. **Total Charges and Tenure**:
Total charges rise as tenure increases. Customers with longer tenure tend to have more services, which raises their total charges.

2. **Demographic Data**:
**Gender** has no noticeable effect on churn. Churn rates for males and females are almost identical.
**Partner and Dependents**:
Customers with partners or dependents are slightly less likely to churn, possibly due to shared service needs.

3. **Service-Related Features**:
  **Fiber optic** internt users have the highest churn.
  Customers **without** add-on services (*security, backup, tech support*) churn more often.

4. **Contract and Billing**:
  **Month-to-month** contracts show the highest churn.
  **Electronic check payments** are linked to higher churn.
  **Automatic payment methods** show better retention.

5. **Tenure**:
Customers with shorter tenure churn more. Retention improves significantly as tenure increases.

## Business Recommendations
| Insight                                      | Business Action                                        |
| -------------------------------------------- | ------------------------------------------------------ |
| Short-tenure customers are at highest risk   | Create onboarding retention offers for new customers   |
| Month-to-month contracts churn more          | Promote one-year and two-year plans with discounts     |
| Electronic check users churn the most        | Encourage automatic payment enrollment                 |
| Customers without add-on services churn more | Bundle support and protection services into promotions |
| Fiber optic users churn frequently           | Investigate service quality or pricing competitiveness |
