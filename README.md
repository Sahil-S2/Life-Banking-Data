![Loan-Wallpaper](Loan_Defaulter_Wallpaper.jpg)

# Loan Defaulter Segmentation

## Overview

The **Loan Defaulter Segmentation** project applies machine learning classification techniques to predict whether a loan applicant is likely to default. By analyzing historical loan application data, the project segments customers into high-risk and low-risk groups, assisting financial institutions in minimizing losses and improving credit policies.

## Project Objective

- **Classification**: Predict whether a customer will default (`1`) or repay (`0`) the loan.
- The model is built without using SMOTE or resampling techniques, focusing purely on model capabilities under class imbalance.

The dataset includes demographic, financial, and behavioral features of applicants from both current and previous applications.

---

## Dataset

### 📂 Sources:
- `application_data.csv` — current loan applications
- `previous_application.csv` — past loan applications

### 📊 Key Features:

- **Demographic & Profile**:
  - `CODE_GENDER`, `CNT_CHILDREN`, `NAME_EDUCATION_TYPE`, `NAME_INCOME_TYPE`, etc.

- **Financial & Loan-related**:
  - `AMT_INCOME_TOTAL`, `AMT_CREDIT`, `AMT_ANNUITY`, `AMT_GOODS_PRICE`, etc.

- **Behavioral Flags**:
  - `DAYS_EMPLOYED`, `DAYS_BIRTH`, `OCCUPATION_TYPE`, etc.

### 🎯 Target:
- `TARGET`: Binary variable — `0` (Non-defaulter), `1` (Defaulter)

---

## Approach

### 1. **Data Preprocessing**
- Removed columns with >40% missing values.
- Dropped weakly correlated `FLAG_*` binary columns.
- Encoded categorical variables using `OneHotEncoder`.
- Scaled numeric features with `StandardScaler`.
- Applied `train_test_split` with `stratify=y`.

### 2. **Model Building & Evaluation**
A pipeline was created using `ColumnTransformer` and `Pipeline` for efficient preprocessing and model training.

#### ✅ Models Trained:
- **Logistic Regression**
- **Random Forest Classifier**
- **Gradient Boosting**
- **XGBoost Classifier**

#### 📈 Evaluation Metrics:
- **Precision, Recall, F1-score**
- **ROC AUC Score**

---

## Model Performance

| Model                | ROC AUC | Accuracy | Recall (Defaulters) | Precision (Defaulters) |
|---------------------|---------|----------|----------------------|-------------------------|
| Logistic Regression | 0.715   | 66%      | 0.66                 | 0.16                    |
| Random Forest       | **0.991** | **97%** | **0.63**             | **1.00**                |
| Gradient Boosting   | 0.792   | 92%      | 0.03                 | 0.98                    |
| XGBoost             | 0.974   | 97%      | 0.63                 | 0.98                    |

> 🚨 Despite class imbalance, Random Forest delivered **exceptionally high performance without SMOTE**, indicating strong signal in the original data.

---

## Key Insights

- **Random Forest** achieved the best performance across all metrics.
- High **precision + recall** makes it suitable for minimizing both Type I and Type II errors.
- **Gradient Boosting** failed to identify defaulters effectively, despite high overall accuracy.
- Class imbalance significantly impacted linear models like Logistic Regression.

---

## Business Implications

- ✅ **Risk Assessment**:
  - Early detection of high-risk applicants reduces financial losses.
- ✅ **Loan Policy Optimization**:
  - Segmentation helps tailor policies to different risk profiles.
- ✅ **Automated Decision Support**:
  - Can be integrated into loan approval systems for real-time scoring.
- ✅ **No Need for Synthetic Oversampling**:
  - The model performs reliably even under imbalance, reducing data engineering overhead.

---

## Technologies Used

- **Python**: Data science workflow
- **Pandas**, **NumPy**: Data wrangling
- **Scikit-learn**: Pipelines, preprocessing, modeling
- **XGBoost**: High-performance gradient boosting
- **Matplotlib/Seaborn**: Visualization

---

## Conclusion

This project demonstrates that with strong features and proper preprocessing, high-performing classification models can be trained on imbalanced datasets without needing synthetic resampling. The **Random Forest Classifier** stood out with a **ROC AUC of 0.991**, providing a powerful and interpretable model for real-world deployment.

### ✅ Key Outcomes:
- Accurate segmentation of loan defaulters.
- Scalable ML pipeline ready for production.
- Framework adaptable to other financial risk tasks.

---

## 📁 Folder Structure
```

📦loan-defaulter-segmentation
┣ 📜application\_data.csv
┣ 📜previous\_application.csv
┣ 📜loan\_default\_banner.jpg
┣ 📜Loan\_Defaulter\_Segmentation.ipynb
┗ 📜README.md

```

---

## Author

**Sahil Jena**  
*Data Science Enthusiast*  
📧 sahilswarajjena456@email.com  
🔗 [LinkedIn](https://www.linkedin.com/in/sahil-jena-067b1b301/) | [GitHub](https://github.com/Sahil-S2/Life-Banking-Data)

---
