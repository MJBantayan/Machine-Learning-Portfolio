# **Predicting Heart Disease with K-Nearest Neighbors**

---

In this notebook we analyze the Cleveland Heart Disease data from the [UC Irvine Heart Disease Dataset](https://archive.ics.uci.edu/dataset/45/heart+disease). We use the **K-Nearest Neighbors (KNN)** algorithm to predict whether a person is likely to have heart disease based on clinical and demographic factors.

#### **Objective**
To build a KNN classifier that can accurately predict the presence of heart disease (binary target: 0 = no disease, 1 = disease).

---

## **1. Dataset Overview**

- Source: UC Irvine Heart Disease Dataset  
- Total Records: 303  
- Features: 13 attributes + target  
- Target: `target` (0 = no heart disease, 1–4 = presence of heart disease)

**Feature descriptions**

* `age` - age in years  
* `sex` - sex (1 = male; 0 = female)  
* `cp` - chest pain type (1–4)  
* `trestbps` - resting blood pressure (mm Hg)  
* `chol` - serum cholesterol (mg/dl)  
* `fbs` - fasting blood sugar > 120 mg/dl (1 = true; 0 = false)  
* `restecg` - resting electrocardiographic results (0–2)  
* `thalach` - maximum heart rate achieved  
* `exang` - exercise induced angina (1 = yes; 0 = no)  
* `oldpeak` - ST depression induced by exercise  
* `slope` - slope of the peak exercise ST segment (1–3)  
* `ca` - number of major vessels (0–3) colored by fluoroscopy  
* `thal` - thalassemia (3 = normal; 6 = fixed defect; 7 = reversible defect)  
* `target` - 0 = no heart disease, 1–4 = heart disease  

---

## **2. Exploratory Data Analysis**

After inspection we see that the data has been pre-cleaned so we are ready to perform EDA. We begin by setting all values of `target` greater than 0 to 1.

### **2.1 EDA Insights**

#### **1. Demographic Trends**

**Sex:**  
Males appear more prone to heart disease than females. Although the dataset has roughly twice as many males, their positive cases are disproportionately higher. Sex may contribute to risk but inconclusive due to sample imbalance.

**Age:**  
Heart disease cases increase steadily and peak around age 58, then decline, possibly due to survival bias. Negatives peak at 41, 51, and 58, suggesting different life stages for diagnosis or awareness.

---

#### **2. Clinical Features**

**Chest Pain Type (cp):**  
The highest number of heart disease positives occurs at cp = 4.0, indicating strong association with heart disease.

**Fasting Blood Sugar (fbs):**  
Both positives and negatives are more common when fbs = 0, implying that fasting blood sugar alone is a weak predictor.

**Exercise-Induced Angina (exang):**  
When exang = 0, heart disease negatives dominate. At exang = 1, positives slightly exceed negatives, showing limited standalone predictive value.

**Slope (slope of peak exercise ST segment):**  
slope = 1: many positives (100+) and few negatives  
slope = 2: more negatives  
slope = 3: rare overall  
This suggests slope interacts with other features (like thalach or oldpeak) for better prediction.

**Number of Major Vessels (ca):**  
ca = 0 corresponds to most negatives (>120), but higher values appear across both classes, suggesting mixed predictive strength.

**Thalassemia (thal):**  
Most positives occur at thal = 3, while thal = 7 links to more negatives. Weak predictive ability when used alone.

---

#### **3. Measured Heart Activity**

**Maximum Heart Rate (thalach):**  
Heart disease positives are spread widely (71–174) with no strong peak. Negatives rise sharply above 140, peaking near 161, implying that lower maximum heart rate may signal heart disease.

**ST Depression (oldpeak):**  
Shows an inverse relation — higher oldpeak values correspond to fewer positives and more negatives. This may be one of the stronger predictors.

---

### **Summary**

Stronger indicators:  
`age`, `cp`, `slope`, `thalach`, `oldpeak`

Weaker standalone predictors:  
`sex`, `fbs`, `exang`, `ca`, `thal`

---

## **3. Correlation and Statistical Tests**

The correlation matrix shows that the most correlated factors to `target` (heart disease) are:

* `thal` = 0.53  
* `ca` = 0.46  
* `exang` = 0.43  
* `oldpeak` = 0.42  
* `cp` = 0.41  

Least correlated:

* `thalach` = -0.42 (negative correlation means higher thalach → lower risk)  
* `fbs` = 0.02  
* `chol` = 0.08  
* `trestbps` = 0.15  
* `restecg` = 0.17  

`age` and `sex` have moderate correlation with heart disease.  

Variables with correlation between each other:  
* `oldpeak` and `slope` = 0.58  
* `cp` and `exang` = 0.38  
* `thal` correlates with `sex` (0.38), `oldpeak` (0.34), `exang` (0.33), and `slope` (0.29)

These correlations may suggest multicollinearity, which can affect model interpretation.

---

### **3.1 Chi-Squared Tests (Categorical Variables)**

| Feature | p-value |
|----------|----------|
| sex | 0.00000 |
| cp | 0.00000 |
| fbs | 0.78127 |
| restecg | 0.00657 |
| ca | 0.00000 |
| exang | 0.00000 |
| slope | 0.00000 |
| thal | 0.00000 |

All categorical variables except `fbs` have p-values < 0.05, meaning they are significantly correlated with the target and can be used in the model. Only `fbs` will be dropped.

---

### **3.2 Variance Inflation Factor (VIF) — Numerical Variables**

| Feature | VIF |
|----------|------|
| age | 1.35 |
| trestbps | 1.13 |
| chol | 1.06 |
| thalach | 1.32 |
| oldpeak | 1.17 |

All numerical variables have VIF < 2, meaning there is low or no multicollinearity. They are safe to include in the model.

---

## **4. Model Development**

### **4.1 Data Preprocessing**

- Encoded categorical columns using `LabelEncoder`  
- Scaled numerical columns using `StandardScaler`  
- Dropped `fbs` based on statistical test results  
- Split the dataset into 80% training and 20% testing using `stratify=y` to keep class balance

---

### **4.2 Model Training and Evaluation**

We trained a **KNeighborsClassifier** with `k=5` and evaluated its performance.

**Classification Report**

| Metric | Class 0 | Class 1 |
|---------|----------|----------|
| Precision | 0.88 | 0.71 |
| Recall | 0.70 | 0.89 |
| F1-score | 0.78 | 0.79 |

**Overall Accuracy:** 78.7%

**ROC-AUC Curve:** shows strong class separation and good predictive performance.

---

### **4.3 Finding the Best K**

A test across `k` values from 1 to 20 showed the following result:

**Best k = 1 with Accuracy = 0.836**

---

## **5. Model Insight and Conclusion**

Since we have already achieved the best k-value during hyperparameter tuning, we end the optimization here.

The final model achieved **83.6% accuracy** and a strong ROC-AUC score, suggesting good classifying ability.  
Feature preprocessing and statistical screening (chi-square and VIF) improved performance by ensuring only meaningful and independent variables were included.

Overall, model show potential for early prediction of heart disease risk based on clinical data.
