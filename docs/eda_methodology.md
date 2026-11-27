# Exploratory Data Analysis (EDA) — Methodology

## 1. Purpose

This document explains **how** the Exploratory Data Analysis (EDA) is organized and performed for the Employee Attrition project. Detailed findings and statistics are documented separately in [`../reports/eda_report.md`](../reports/eda_report.md).

## 2. Files and Tools

| Item | Location / Tool |
|---|---|
| Original dataset | `data/raw/WA_Fn-UseC_-HR-Employee-Attrition.csv` |
| Analysis notebook | `notebooks/final_eda.ipynb` |
| EDA findings | `reports/eda_report.md` |
| Main tools | Python, pandas, matplotlib, Jupyter Notebook |

The original CSV is kept unchanged during EDA.

## 3. EDA Workflow

| Step | What we do | Why it matters |
|---|---|---|
| Load and inspect | Read the CSV; review the first rows, dimensions, columns, and data types. | Understand the dataset structure. |
| Check data quality | Check missing values, duplicate records, unique employee IDs, constant columns, placeholder text, and basic logical rules. | Identify issues before preprocessing. |
| Explore distributions | Review numerical and categorical summaries. | Understand typical values, ranges, and group sizes. |
| Analyze the target | Count `Attrition = Yes/No` and calculate the attrition rate. | Understand the prediction target and class balance. |
| Compare features with attrition | Compare category-level attrition rates and numerical summaries; use selected charts. | Find patterns worth investigating. |
| Review relationships | Examine correlations among numerical columns and with an encoded attrition indicator. | Flag potentially related or overlapping features. |
| Identify possible outliers | Review boxplots and IQR-based outlier counts. | Flag unusual values for later investigation. |
| Prepare feature candidates | List potential model inputs without changing the original data. | Inform the next preprocessing phase. |

### Features explored

Examples include `OverTime`, `Department`, `JobSatisfaction`, `WorkLifeBalance`, `BusinessTravel`, `JobRole`, `Age`, `MonthlyIncome`, and `YearsAtCompany`, alongside other categorical and numerical columns.

### Comparison approach

- For categorical features, compare **attrition percentages within each group** and consider group sizes.
- For numerical features, compare group statistics such as mean and median, and examine distributions where useful.
- Treat correlations and observed differences as **associations, not proof of causation**.

## 4. Initial Feature Plan

- **Prediction target:** `Attrition`.
- **Employee identifier:** Keep `EmployeeNumber` for employee lookup, but not as a model input.
- **Constant columns:** Exclude `EmployeeCount`, `Over18`, and `StandardHours` from model inputs because they do not vary between employees.
- **Other columns:** Keep the remaining columns as **initial candidates**, subject to preprocessing, validation, and model evaluation.

This leaves **30 initial candidate feature columns** out of the dataset's 35 columns. This is a starting list, not the final feature selection.

## 5. What EDA Does Not Do

EDA does **not** modify the raw dataset, automatically remove outliers, encode categories, or train machine learning models. Those tasks belong to later phases. An unusual value should be investigated before any decision to change or remove it.

## 6. Reproducing the Analysis

1. Keep the source CSV in `data/raw/` with the filename shown above.
2. Open `notebooks/final_eda.ipynb` in a Jupyter-enabled Python environment with `pandas` and `matplotlib` available.
3. Run the notebook cells in order and review any errors or unexpected results.
4. Read `reports/eda_report.md` for the findings and recommendations.

**Path note:** The notebook's relative input path (`../data/raw/...`) assumes its working directory is `notebooks/`. If the notebook runs from the repository root, adjust the path accordingly.

## 7. Next Phase

Use the EDA findings to define the **Data Cleaning and Preprocessing** plan. Any feature transformation that learns from the dataset will be handled carefully in the modeling workflow to avoid data leakage.
