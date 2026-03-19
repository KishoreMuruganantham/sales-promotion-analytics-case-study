```text
   _____       _                 _____                           _   _
  / ____|     | |               |  __ \                         | | (_)
 | (___   __ _| | ___  ___      | |__) | __ ___  _ __ ___   ___ | |_ _  ___  _ __
  \___ \ / _` | |/ _ \/ __|     |  ___/ '__/ _ \| '_ ` _ \ / _ \| __| |/ _ \| '_ \
  ____) | (_| | |  __/\__ \     | |   | | | (_) | | | | | | (_) | |_| | (_) | | | |
 |_____/ \__,_|_|\___||___/     |_|   |_|  \___/|_| |_| |_|\___/ \__|_|\___/|_| |_|

  _                _       _   _
   / \   _ __   __ _| |_   _| |_(_) ___ ___
  / _ \ | '_ \ / _` | | | | | __| |/ __/ __|
 / ___ \| | | | (_| | | |_| | |_| | (__\__ \
/_/   \_\_| |_|\__,_|_|\__, |\__|_|\___|___/
            |___/
```

# Sales and Promotion Analytics Case Study

Retail analytics case study built for a Springboard statistics and EDA assignment. This project combines weekly store-level sales data with monthly promotion and demographic data to identify performance drivers, clean and align the raw sources, and prepare a forecasting-ready dataset for downstream modeling

## Repository

Repository name: `sales-promotion-analytics-case-study`

This repository contains:

- A Kaggle-ready notebook
- Both raw datasets used in the assignment
- The original assignment PDFs
- A documented workflow from data understanding through modeling preparation

## Project Scope

This is not just a notebook with charts. The work is structured to answer the full assignment properly:

- Include explicit data understanding and business framing
- Inspect and validate the raw datasets
- Resolve missing values, inconsistent categories, and merge risks
- Reconcile weekly sales data with monthly promotion data
- Analyze numeric, categorical, and time-based sales patterns
- Engineer features suitable for predictive modeling
- Prepare a leakage-aware modeling table with time-based validation
- Export cleaned datasets for submission deliverables
- Solve the separate hypothesis testing questions included in the second document

## Business Questions Addressed

- Which features appear to have the strongest relationship with weekly sales?
- Does higher promotion spend align with better sales outcomes?
- Which store types consistently outperform others?
- Which regions show stronger or weaker performance?
- Which engineered features are most useful for a future sales model?

## Project Structure

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

## Dataset Summary

### Sales dataset

- Grain: store-week
- Key fields: `store_id`, `week_start_date`, `weekly_sales`, `store_area`, `num_employees`, `store_type`

### Promotion and demographics dataset

- Grain: store-month
- Key fields: `store_id`, `month`, `promotion_budget`, `median_income`, `population_density`, `region`

## Notebook Workflow

The notebook is organized into these sections:

1. Executive summary and assignment framing
2. Data understanding
3. Data cleaning and preparation
4. Exploratory data analysis
5. Business insights and recommendations
6. Feature engineering
7. Data preparation for modeling
8. Hypothesis testing

## Technical Approach

### Cleaning strategy

- Parse dates explicitly and normalize merge keys
- Drop duplicate rows
- Standardize missing and inconsistent categorical values
- Impute feature gaps using store-level logic first, then broader fallback rules
- Preserve missing target values as missing rather than fabricating sales values

### Merge strategy

The main challenge in this assignment is the mismatch in data granularity:

- Sales data is weekly
- Promotion and demographic data is monthly

The notebook handles this by converting each weekly sales record into a month-start timestamp and then merging on `store_id` and month with a `many_to_one` constraint. That makes the alignment explicit and guards against accidental duplication during the merge.

### Feature engineering strategy

- Lagged sales features
- Rolling sales averages
- Log-transformed promotion budget
- Budget intensity measures
- Income and density interaction terms
- Bucketed store-size and market-profile categories

### Modeling preparation strategy

- Time-based train/test split instead of random split
- `TimeSeriesSplit` for cross-validation
- Median imputation and scaling for numeric predictors
- Most-frequent imputation and one-hot encoding for categorical predictors
- Leakage-aware exclusion of non-feature and target-derived fields

## Kaggle Usage

The notebook is designed to run in Kaggle with these input paths:

- `/kaggle/input/datasets/mkishore129/promo-demo-dataset/sales_dataset.csv`
- `/kaggle/input/datasets/mkishore129/promo-demo-dataset/promo_demo_dataset.csv`

### Run steps

1. Upload the notebook to Kaggle.
2. Attach the CSV files as Kaggle inputs.
3. Confirm the input paths match the two paths above.
4. Run all cells.
5. Download the generated outputs from `/kaggle/working` if needed.

## Generated Outputs

When executed, the notebook writes:

- `cleaned_sales_dataset.csv`
- `cleaned_promo_demo_dataset.csv`
- `cleaned_merged_sales_dataset.csv`
- `final_modeling_dataset.csv`

These match the cleaned-data and modeling-preparation deliverables required by the assignment.

## Deliverable Coverage

The notebook now covers the full assignment more explicitly:

- data understanding discussion
- cleaning decisions and merge justification
- visual analysis tied to business questions
- business insights and recommendations
- feature engineering and modeling-readiness explanation
- cleaned and modeling-ready dataset exports
- hypothesis testing solutions from the second document

## Hypothesis Testing Coverage

The notebook also solves the separate hypothesis testing tasks from the second assignment document:

- One-way ANOVA
- Independent two-sample t-test
- Chi-square test of independence
- Paired t-test

## Libraries Used

- Python
- pandas
- NumPy
- matplotlib
- seaborn
- SciPy
- scikit-learn

## Why This Repository Works

The goal here is to make the submission both assignment-ready and readable by another analyst. The structure is intended to show:

- clear reasoning about data quality
- defensible preprocessing choices
- business-focused EDA
- forecasting-aware feature engineering
- statistically correct treatment of the hypothesis-testing section

## Author

Kishore Muruganantham
