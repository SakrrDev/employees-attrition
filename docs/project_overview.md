# Project Overview

**Project:** Employee Attrition Analytics & Retention Analysis  
**Dataset:** IBM HR Analytics Employee Attrition & Performance (synthetic)

## 1. Overview

This project explores employee attrition patterns and develops an interactive HR analytics and retention-risk application. It combines exploratory data analysis, machine learning, and a simple website to help HR users review employee information and model estimates.

## 2. Objectives

- Understand employee attrition patterns and related employee characteristics.
- Train and evaluate machine-learning models that estimate attrition risk.
- Present clear HR statistics through an interactive dashboard.
- Show employee-level predictions with understandable model explanations.

## 3. Dataset

| Item | Description |
|---|---|
| Dataset | IBM HR Analytics Employee Attrition & Performance |
| Employee records | 1,470 |
| Columns | 35 |
| Prediction target | `Attrition` (`Yes` / `No`) |
| Data | Synthetic employee data; not real HR records |

## 4. Main Application Features

### HR Analytics Dashboard

- Employee totals and overall attrition rate.
- Attrition comparisons by department, overtime status, and job satisfaction.
- Clear charts and summaries for HR exploration.

### Employee Retention Analysis

- Search for a record using `EmployeeNumber`.
- View employees ranked by their estimated attrition risk (for example, the top 5 or 10).
- View an employee overview and a model-based risk analysis report.
- Review factors influencing the prediction, without treating them as proven causes.

## 5. MVP Approach

The initial application is planned as an **interactive website using a static dataset and precomputed model predictions**. Login, a live database, a separate backend, and real-time inference are outside the initial scope.

## 6. Limitations

- Model predictions are estimates, not guarantees or confirmed reasons for leaving.
- The dataset is synthetic; findings are not validated for real employees.
- The application is intended to support human review, not automate employment decisions.

## Related Documents

- [Project Roadmap](project_roadmap.md)
- [Folder Structure](folder_structure.md)
- [EDA Report](../reports/eda_report.md)
