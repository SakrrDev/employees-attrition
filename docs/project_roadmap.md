# Project Roadmap

**Project:** Employee Attrition Analytics & Retention Analysis

The roadmap is organized into ten phases. Some work may happen in parallel, but dependencies should be respected.

| Phase | Workstream | Main goal |
|:---:|---|---|
| 01 | Scope & Feasibility | Define the problem, users, objectives, and MVP boundaries. |
| 02 | Project Planning | Organize phases, repository structure, and workflow. |
| 03 | Data Understanding & EDA | Inspect data quality and explore relationships with attrition. |
| 04 | Data Preparation & Feature Engineering | Clean, encode, and prepare features for modeling. |
| 05 | Model Development | Train and compare candidate machine-learning models. |
| 06 | Model Evaluation | Evaluate results and select a suitable model. |
| 07 | Model Explainability | Explain risk estimates and prepare predictions. |
| 08 | Analytics Data Preparation | Prepare statistics and application-ready datasets. |
| 09 | Frontend Implementation | Build the interactive HR dashboard and employee pages. |
| 10 | Testing & Delivery | Test the complete application and finalize project outputs. |

## Key Dependencies

- **EDA before cleaning decisions:** Data quality and distributions guide preparation.
- **Preprocessing before modeling:** Model inputs must be consistently prepared, without data leakage.
- **Evaluation before use:** A trained model is not ready for application use until evaluated.
- **Precomputed results before integration:** The frontend will read prepared dashboard data and predictions.

## Working Principles

- Preserve the original dataset in `data/raw/`.
- Keep notebooks readable, with Markdown headings and focused code cells.
- Document important findings and decisions as work progresses.
- Work in Git branches and review changes through pull requests.

## Current Work

**Phase 03 — Data Understanding & EDA:** Review the notebook and its results, finalize the [EDA Report](../reports/eda_report.md), and prepare the changes for a pull request. **Phase 04** starts after the EDA findings and cleaning plan are reviewed.
