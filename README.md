# SQL Revenue Analysis & Forecasting — Synthetic E-commerce Demo

**Python • SQLite • Business analytics • Revenue metrics • Predictive baseline**

This README describes the executable e-commerce analysis currently saved in [us_migration_prediction.ipynb](us_migration_prediction.ipynb).

**Scope note:** the repository name and earlier notebook narrative refer to U.S. migration. The saved executed code instead generates synthetic sales and analyzes monthly revenue. A validated migration forecasting pipeline is not demonstrated by the current committed contents.

## Problem

How can SQL turn transaction data into monthly revenue and customer metrics, and how well does a simple regression baseline forecast the resulting revenue series?

## Data

The code generates **1,000 synthetic orders**, with customer IDs, randomly selected dates from a 500-day window starting in 2022, and randomly generated order amounts. These are fictional sales, not real commercial or migration records.

## Methodology

1. Create a SQLite `sales` table and insert the generated orders.
2. Aggregate monthly revenue with `SUM(amount)` and distinct customers with `COUNT(DISTINCT customer_id)`.
3. Use a sequential month number as the linear-regression feature.
4. Split the monthly records into chronological training and test sets with `shuffle=False`.
5. Evaluate the holdout predictions, plot history and a six-month forecast, and export CSVs.

## Technologies

**Python, SQLite, SQL, Pandas, NumPy, Matplotlib, scikit-learn, Google Colab.**

## Results and interpretation

The saved output reports **MSE ≈ 17,095,821.51** and **R² ≈ −0.262**. The negative R² indicates that the fitted predictions perform worse than a constant test-set-mean benchmark under this metric. The forecast is a demonstration of the workflow, not a validated planning tool.

The most useful portfolio evidence is the SQL aggregation of revenue and customers, the reproducible synthetic-data setup, and the transparent evaluation of a predictive baseline. No revenue improvement or commercial impact has been established.

## Explore and reproduce

Open the notebook and review the executed e-commerce cell. It creates `ecommerce.db` and writes `output/historical_data.csv` and `output/future_forecast.csv` when run; those outputs are generated artifacts, not files currently committed at the repository root.

**Use a separate working directory:** the current code removes an existing local file named `ecommerce.db` before creating its demo database.

## Next steps

Separate the migration narrative from the e-commerce implementation, compare forecasting baselines, and use documented real data if the project is extended for a business use case. A Power BI dashboard is a possible extension, not a current feature.
