# Folder Structure

A quick guide to where each part of the project belongs.

## Project Tree

```text
employees-attrition/
├── data/
│   ├── raw/
│   └── processed/
├── notebooks/
├── src/
│   ├── data/
│   ├── ml/
│   └── analytics/
├── models/
├── reports/
├── docs/
├── web/
└── README.md
```

## Folder Purposes

| Folder / File | What goes here? |
|---|---|
| `data/raw/` | Original, unchanged datasets. |
| `data/processed/` | Prepared datasets produced in later phases. |
| `notebooks/` | Exploratory analysis notebooks, including `final_eda.ipynb`. |
| `src/data/` | Reusable cleaning, preprocessing, and feature code. |
| `src/ml/` | Model training, evaluation, prediction, and explanation code. |
| `src/analytics/` | Code to prepare dashboard statistics and data. |
| `models/` | Saved trained models or pipelines. |
| `reports/` | Analysis findings, model results, and charts. |
| `docs/` | Project overview, roadmap, structure, and decisions. |
| `web/` | Interactive website code and assets. |
| `README.md` | Short project introduction and links to important files. |

Add files and subfolders only when they are needed. Empty folders are not tracked by Git unless they contain a file.
