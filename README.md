#  ____        _                 ____                                      _   _
# / ___|  __ _| | ___  ___      |  _ \ _ __ ___  _ __ ___   ___  ___ _ __ | |_(_) ___  _ __
# \___ \ / _` | |/ _ \/ __|_____| |_) | '__/ _ \| '_ ` _ \ / _ \/ __| '_ \| __| |/ _ \| '_ \
#  ___) | (_| | |  __/\__ \_____|  __/| | | (_) | | | | | | (_) \__ \ | | | |_| | (_) | | | |
# |____/ \__,_|_|\___||___/     |_|   |_|  \___/|_| |_| |_|\___/|___/_| |_|\__|_|\___/|_| |_|
#
#    _                _       _   _
#   / \   _ __   __ _| |_   _| |_(_) ___ ___
#  / _ \ | '_ \ / _` | | | | | __| |/ __/ __|
# / ___ \| | | | (_| | | |_| | |_| | (__\__ \
#/_/   \_\_| |_|\__,_|_|\__, |\__|_|\___|___/
#                       |___/

## Sales and Promotion Analytics Case Study

End-to-end retail analytics project for a Springboard statistics and EDA assignment. This repository contains the Kaggle-ready notebook, source datasets, and assignment documents used to analyze weekly store sales against promotion spending and demographic context.

## Repository Title

`sales-promotion-analytics-case-study`

## Project Goals

- Clean and validate weekly sales and monthly promotion-demographic data.
- Resolve granularity differences between weekly and monthly sources.
- Perform exploratory data analysis to identify business drivers of sales.
- Engineer forecasting-friendly features while avoiding target leakage.
- Prepare a final modeling-ready dataset for downstream machine learning.
- Solve the separate hypothesis testing problems included in the assignment.

## Repository Structure

```text
Springboard - Stats & EDA - Level 4 - Assignment/
|-- README.md
|-- .gitignore
`-- Level 4/
    |-- DS Springboard - Stats - Level 4 -Assignment.pdf
    |-- Level 4 - Hypothesis Testing.pdf
    |-- promo_demo_dataset.csv
    |-- sales_dataset.csv
    `-- sales-and-promotion-analytics-case-study.ipynb
```

## Notebook Contents

The notebook is organized into a full business-analysis workflow:

1. Data understanding
2. Data cleaning and preparation
3. Exploratory data analysis
4. Feature engineering
5. Modeling preparation with time-aware validation
6. Business recommendations
7. Hypothesis testing solutions

## Datasets

### Sales Dataset

- Grain: store-week
- Key fields: `store_id`, `week_start_date`, `weekly_sales`, `store_area`, `num_employees`, `store_type`

### Promotion and Demographics Dataset

- Grain: store-month
- Key fields: `store_id`, `month`, `promotion_budget`, `median_income`, `population_density`, `region`

## Analysis Highlights

- Weekly sales are aligned to monthly promotion records using month-start timestamps.
- Missing feature values are handled with store-level and broader fallback imputations.
- Categorical inconsistencies are standardized before merge.
- Time-based feature engineering includes lag and rolling-window sales signals.
- Train and test sets are split chronologically to match real forecasting conditions.
- Cross-validation uses `TimeSeriesSplit` rather than random folds.

## Kaggle Run Instructions

1. Upload the notebook to Kaggle.
2. Attach the two CSV files as Kaggle inputs.
3. Confirm these paths inside the notebook:
   - `/kaggle/input/datasets/mkishore129/promo-demo-dataset/sales_dataset.csv`
   - `/kaggle/input/datasets/mkishore129/promo-demo-dataset/promo_demo_dataset.csv`
4. Run all cells.
5. Collect generated outputs from `/kaggle/working`.

## Generated Outputs

When executed in Kaggle, the notebook writes:

- `cleaned_merged_sales_dataset.csv`
- `final_modeling_dataset.csv`

## Business Questions Addressed

- Which factors have the strongest relationship with sales?
- Does promotion spending correlate with stronger sales performance?
- Which regions and store types outperform the rest?
- What engineered features are most useful for forecasting future sales?

## Statistical Tests Included

The notebook also solves four separate hypothesis-testing tasks:

- One-way ANOVA
- Independent two-sample t-test
- Chi-square test of independence
- Paired t-test

## Tools and Libraries

- Python
- pandas
- NumPy
- seaborn
- matplotlib
- SciPy
- scikit-learn

## Notes

- The notebook is intended to be run in Kaggle and is not pre-executed in this repository.
- The repository keeps the original assignment PDFs alongside the analysis assets for traceability.

## Author

Kishore Muruganantham