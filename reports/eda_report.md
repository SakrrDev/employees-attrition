# Employee Attrition — EDA Report

**Project:** Employee Attrition Analytics & Retention Analysis  
**Dataset:** IBM HR Analytics Employee Attrition & Performance (synthetic)  
**Notebook:** [`notebooks/final_eda.ipynb`](../notebooks/final_eda.ipynb)  
**Phase:** 03 — Data Understanding & Exploratory Data Analysis

## 1. Objective

Explore employee data, check data quality, and identify patterns associated with employee attrition. The findings will guide data preparation and machine learning. **No data cleaning or model training is performed in this phase.**

## 2. Dataset Overview

| Item | Result |
|---|---:|
| Employee records | 1,470 |
| Columns | 35 |
| Numerical columns (`int64`) | 26 |
| Text columns (`object`) | 9 |
| Employees who stayed (`Attrition = No`) | 1,233 (83.88%) |
| Employees who left (`Attrition = Yes`) | 237 (16.12%) |

The target is **imbalanced**: employees who left represent only 16.12% of the data. Model evaluation will need metrics beyond accuracy.

## 3. Data Quality Findings

| Check | Result |
|---|---|
| Missing values | None detected |
| Duplicate rows | 0 |
| Duplicate `EmployeeNumber` values | 0 |
| Common missing-value placeholders in text columns | None detected |
| Constant columns | `EmployeeCount`, `Over18`, `StandardHours` |
| Checked tenure inconsistencies | 0 |

The tenure checks found no cases where `YearsAtCompany` exceeds `TotalWorkingYears`, or where `YearsInCurrentRole`, `YearsSinceLastPromotion`, or `YearsWithCurrManager` exceeds `YearsAtCompany`.

These checks cover common issues but do not guarantee that all records are error-free.

## 4. Main Attrition Findings

**Attrition rate = (employees who left / employees in the group) × 100.** Group rates are used instead of raw counts to make comparisons clearer.

### 4.1 Key Categorical Features

| Feature | Group | Employees | Left | Attrition rate |
|---|---|---:|---:|---:|
| `OverTime` | Yes | 416 | 127 | **30.53%** |
| `OverTime` | No | 1,054 | 110 | 10.44% |
| `Department` | Sales | 446 | 92 | **20.63%** |
| `Department` | Research & Development | 961 | 133 | 13.84% |
| `JobSatisfaction` | 1 — Low | 289 | 66 | **22.84%** |
| `JobSatisfaction` | 4 — Very High | 459 | 52 | 11.33% |
| `WorkLifeBalance` | 1 — Bad | 80 | 25 | **31.25%** |
| `BusinessTravel` | Travel_Frequently | 277 | 69 | **24.91%** |
| `BusinessTravel` | Non-Travel | 150 | 12 | 8.00% |
| `JobRole` | Sales Representative | 83 | 33 | **39.76%** |

**Observations:** Higher attrition rates appear among employees who work overtime, travel frequently, report low job satisfaction, or report poor work-life balance. Sales Representatives have a high rate, but their group contains only 83 employees. Group sizes matter when interpreting these differences.

### 4.2 Numerical Features

| Feature | Median: Stayed | Median: Left |
|---|---:|---:|
| `MonthlyIncome` | 5,204 | 3,202 |
| `Age` | 36 | 32 |
| `YearsAtCompany` | 6 | 3 |
| `TotalWorkingYears` | 10 | 7 |
| `DistanceFromHome` | 7 | 9 |

**Observation:** Employees who left tended to be younger, have lower monthly income, and have shorter work experience and company tenure. They also had a higher median distance from home.

### 4.3 Feature Relationships and Potential Outliers

- `MonthlyIncome` and `JobLevel` are strongly correlated (**Pearson r ≈ 0.95**). Their relationship should be considered during modeling, but neither should be removed automatically.
- The **1.5 × IQR** rule flagged **114** potential outliers in `MonthlyIncome`, **63** in `TotalWorkingYears`, and **104** in `YearsAtCompany`.
- The same rule found **0** potential outliers in `Age` and `DistanceFromHome`.

These are **statistical flags, not confirmed data errors**. High salaries and long careers may be valid, so no rows should be deleted based on the IQR check alone.

## 5. Initial Feature and Cleaning Plan

| Columns / issue | Proposed action | Reason |
|---|---|---|
| `Attrition` | Use as the target, not an input feature | This is what the model predicts |
| `EmployeeNumber` | Keep for employee lookup; exclude from model inputs | It is an identifier |
| `EmployeeCount`, `Over18`, `StandardHours` | Exclude from model inputs | They have only one value |
| Categorical columns such as `Department`, `JobRole`, `OverTime`, `BusinessTravel` | Encode during preprocessing | Models need suitable input representations |
| Numeric columns such as `Age`, `MonthlyIncome`, `YearsAtCompany` | Keep as initial candidates | They may contain useful information |
| Potential outliers | Review and retain unless there is a justified reason to change them | Extreme values may be valid |
| Strongly correlated columns | Review during model development | Avoid removing useful information too early |
| Target imbalance | Use stratified evaluation and minority-class metrics | Accuracy alone may be misleading |

**Initial feature count:** 30 candidate input columns after excluding the target, employee ID, and three constant columns. This is a starting list, **not the final selected feature set**.

Data-dependent preprocessing must be fitted on training data only and then applied consistently to validation/test data. We will address this in the next phase to avoid data leakage. Sensitive attributes should be reviewed for fairness and appropriate use before any HR decision support is built.

## 6. Limitations

- The dataset is **synthetic** and does not represent real company outcomes.
- These findings show **associations, not causes** of employee departure.
- EDA alone does not prove that any feature improves prediction.
- No model performance or real-world retention benefit has been established yet.
- The dataset does not show when a person left, so it cannot directly estimate time until departure.

## 7. Next Phase

Proceed to **Data Preparation & Feature Engineering**. Keep the raw CSV unchanged, implement the agreed preprocessing steps, and then evaluate candidate machine-learning models.
