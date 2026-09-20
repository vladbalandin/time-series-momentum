# Data

The notebook uses fixed local data snapshots so that the research sample does not change between runs. The Fama/French factors file is included in this repository. The two Yahoo Finance price snapshots used in the analysis are kept locally and are not redistributed in the public repository.

| File | Source | Public repository |
| --- | --- | --- |
| `sp500tr_daily_1988_2026-07.csv` | [Yahoo Finance — `^SP500TR`](https://finance.yahoo.com/quote/%5ESP500TR/history/) | Not included |
| `spy_daily_1993_2026-07.csv` | [Yahoo Finance — SPY](https://finance.yahoo.com/quote/SPY/history/) | Not included |
| `F-F_Research_Data_Factors.csv` | [Kenneth R. French Data Library](https://mba.tuck.dartmouth.edu/pages/faculty/ken.french/data_library.html) | Included |

## S&P 500 Total Return Index

The research snapshot contains 9,717 daily `^SP500TR` observations from January 4, 1988 through July 31, 2026. The notebook uses `Close`, removes the timezone, and resamples the series to month-end.

The local file must be named:

```text
sp500tr_daily_1988_2026-07.csv
```

## SPY

The original SPY snapshot was downloaded with:

```python
yfinance.Ticker("SPY").history(period="max", auto_adjust=False)
```

It contains 8,433 daily observations from January 29, 1993 through July 31, 2026. The notebook uses `Adj Close` for monthly holding-period returns and removes the timezone before resampling.

The local file must be named:

```text
spy_daily_1993_2026-07.csv
```

## Risk-free rate

`F-F_Research_Data_Factors.csv` comes from the Kenneth R. French Data Library. The notebook reads the monthly `RF` series using `header=3`, `nrows=1201`, and `usecols=["Unnamed: 0", "RF"]`. The monthly block runs from July 1926 through July 2026. `RF` is expressed in percent and is divided by 100 before use.

## Reproducibility note

The saved notebook outputs were produced from the three fixed snapshots described above. A fresh Yahoo Finance download may contain revisions or different adjusted prices, so it should not be expected to reproduce the saved results exactly.
