# 📝 Customer Churn Analysis Report

## 1. Project Overview
- **Objective**: Analyze customer data to identify factors that drive churn.
- **Dataset**: Contains customer demographics, account information, and churn status.
- **Goal**:
  - Understand which segments have higher churn rates.
  - Visualize patterns using charts (countplots, stacked bar charts, etc.).
  - Generate actionable insights to reduce churn.

---

## 2. Dataset Summary
Key columns (example):
- `gender`: Male / Female
- `SeniorCitizen`: 0 / 1
- `Partner` / `Dependents`
- `tenure` (months)
- `PhoneService`, `InternetService`, `Contract`
- `MonthlyCharges` / `TotalCharges`
- `Churn` (Yes / No)

---

## 3. Data Cleaning & Preparation
- Checked for **null values** and handled missing `TotalCharges`.
- Converted categorical variables to appropriate types.
- Ensured numerical variables are correctly formatted.
- Created new features like **tenure groups** if needed.

---

## 4. Exploratory Data Analysis (EDA)
We used **Seaborn** and **Matplotlib** for visualizations:

### 4.1 Univariate Analysis
- Countplots of gender, contract types, and internet services.
- Histograms for tenure and charges.

### 4.2 Bivariate Analysis (with Churn)
- Compared churn rate across demographic & service features.
- Example: `sns.countplot(x='gender', hue='Churn', data=df)` to see churn split by gender.

### 4.3 Stacked Bar Charts with Percentages
We converted count data into **percentages** to understand churn proportionally:

```python
counts = df.groupby(['gender','Churn']).size().unstack(fill_value=0)
percentages = counts.div(counts.sum(axis=1), axis=0) * 100
# (Plotted stacked bars with percentage labels)


📊 Insight: This revealed that although absolute churn counts may differ, the churn rate within each gender is comparable (or highlight your finding).

5. Key Insights

Contract Type: Customers on month-to-month contracts show the highest churn rates.

Tenure: New customers (low tenure) churn more frequently.

Charges: Higher monthly charges tend to correlate with higher churn probability.

Internet Service: Fiber optic customers show higher churn than DSL.

(Replace with your actual findings after running the notebook.)

6. Business Recommendations

Incentivize long-term contracts with discounts.

Improve onboarding & engagement for new customers.

Offer retention incentives to high-risk segments identified from the analysis.

Revisit pricing models or improve service for high-charge customers.

7. Visualizations Included

Countplots by demographic variables.

Stacked Bar Charts showing percentage churn by gender, contract type, internet service.

Histograms and KDE plots for numeric variables.

Correlation heatmaps for numeric features.

8. Tools & Libraries

Python 3.x

Pandas for data wrangling

Matplotlib / Seaborn for visualization

Jupyter Notebook for analysis


10. How to Run
pip install -r requirements.txt
jupyter notebook notebooks/a_customer_churn_project_in_DA.ipynb
