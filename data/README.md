# Input snapshots

Use the original files with the exact names below. The notebook reads local snapshots and does not download replacement data automatically.

| File | Status | Required content |
| --- | --- | --- |
| `sp500tr_daily_1988_2026-07.csv` | Included, unchanged | Daily `^SP500TR` data; `Date`, `Close`, `Open`, `High`, `Low`, `Volume`, `Dividends`, and `Stock Splits` columns |
| `F-F_Research_Data_Factors.csv` | Included, unchanged | Original factors file; the notebook uses the date field and monthly `RF` column |
| `spy_daily_1993_2026-07.csv` | Included, unchanged | Original daily SPY snapshot; `Date` and `Adj Close` columns |

The index snapshot has 9,717 daily rows, from January 4, 1988 through July 31, 2026. The original notebook converted its date index to UTC, removed the timezone, and resampled to month-end. That sequence is preserved.

The factors loader uses `header=3`, `nrows=1201`, and `usecols=["Unnamed: 0", "RF"]`, as in the original notebook. The monthly block runs from July 1926 through July 2026. `RF` is expressed in percent and is divided by 100. The supplied file header identifies its one-month Treasury bill series; no annual-yield conversion is used.

The original SPY download used `yfinance.Ticker("SPY").history(period="max", auto_adjust=False)`, ended at July 31, 2026, and removed the timezone before saving. The included snapshot has 8,433 daily rows, from January 29, 1993 through July 31, 2026. Its `Adj Close` column supplies the monthly holding-period returns. No synthetic data or fresh replacement download is used.

All three snapshots were used to rerun the complete research calculation. Keep these files unchanged to reproduce the saved results. A newer download may contain data revisions or different adjusted prices and should not be assumed to reproduce the same results exactly.
