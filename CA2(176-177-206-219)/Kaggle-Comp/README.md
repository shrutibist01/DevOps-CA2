
# DevOps - CA 2 Kaggle Challenge
# Store Sales - Time Series Forecasting

### By:

- Samidha Manjrekar (22070122176)
- Samruddhi Borhade (22070122177)
- Shruti Bist (22070122206)
- Srishti Parulekar (22070122219)

This notebook presents a simple yet effective baseline model for the **[Store Sales - Time Series Forecasting](https://www.kaggle.com/competitions/store-sales-time-series-forecasting)** competition.  
The goal is to **predict daily sales for different stores and product families** using historical data and related external factors.

---

## Dataset

Files available in `/kaggle/input/store-sales-time-series-forecasting/`:

| File Name | Description |
|------------|-------------|
| `train.csv` | Historical daily sales data |
| `test.csv` | Data for which predictions are required |
| `stores.csv` | Store metadata |
| `oil.csv` | Daily oil prices |
| `holidays_events.csv` | Holiday and event information |
| `transactions.csv` | Daily transactions for each store |
| `sample_submission.csv` | Sample submission format |

---

## Approach

A **median-based forecasting model** was used as a starting point:

1. Compute the **median sales** per `(store_nbr, family)` (or extended groups) using the `train` dataset.  
2. Merge these medians with the `test` data.  
3. Fill missing values using appropriate fallbacks (e.g., median by store+family+day_of_week, then global median).  
4. Evaluate performance using **Root Mean Squared Logarithmic Error (RMSLE)** on a time-based validation split.

This serves as a simple yet strong baseline for further experimentation.

---

## Results

| Dataset | RMSLE |
|------------|-------------|
| Local Validation  | 1.0267 |
| Public Leaderboard after submission | 1.08776 |
