# Time-Series Momentum in the S&P 500

An empirical study of time-series momentum in the S&P 500 Total Return Index using Python.

## Overview

This project investigates whether past market performance contains information about subsequent returns in the S&P 500.

The main research question is:

**If the S&P 500 has generated a positive return over the previous 12 months, are subsequent returns systematically higher?**

The project is inspired by the time-series momentum literature, particularly Moskowitz, Ooi & Pedersen (2012), and combines statistical testing with a simple systematic trading strategy.

## Data

The analysis uses historical daily data for the **S&P 500 Total Return Index**, including reinvested dividends, covering approximately 1988–2026.

Daily observations are converted to month-end frequency for the main analysis.

Risk-free returns used in the backtest are obtained from the **Fama-French Research Data Factors** dataset.

## Methodology

The analysis includes:

- Data cleaning and conversion from daily to monthly observations
- Construction of trailing 12-month momentum signals
- Calculation of 1-month and 3-month forward returns
- Conditional return comparisons after positive and non-positive momentum signals
- Welch-style hypothesis testing
- OLS regression analysis
- HAC / Newey-West standard errors to account for heteroskedasticity and serial dependence
- Systematic strategy backtesting
- Risk-adjusted performance evaluation
- Crisis-period analysis
- Robustness checks across 6-, 9-, 12-, and 18-month lookback windows

## Main Findings

The data show a positive relationship between past and subsequent market returns.

For the 3-month horizon, the average subsequent S&P 500 Total Return was approximately **2.36 percentage points higher** following a positive 12-month return than following a non-positive one.

A naive OLS regression suggests statistical significance. However, 3-month forward returns overlap, creating substantial serial correlation. After applying HAC / Newey-West standard errors, the coefficient is no longer statistically significant across reasonable lag specifications.

This suggests that the sample contains a **momentum-like pattern**, but the statistical evidence is not strong enough to reject the null hypothesis once serial dependence is taken into account.

## Strategy Backtest

A simple monthly strategy is constructed using the momentum signal:

- **Positive momentum:** invested in the S&P 500 Total Return Index
- **Non-positive momentum:** invested at the risk-free rate

The strategy is evaluated using:

- Compound Annual Growth Rate (CAGR)
- Annualized volatility
- Sharpe ratio
- Maximum drawdown
- Cumulative wealth

For the 12-month signal, the robustness-period backtest produced approximately:

| Metric | Momentum Strategy | Benchmark |
|---|---:|---:|
| CAGR | 11.2% | 11.0% |
| Annualized Volatility | 11.8% | 14.7% |
| Sharpe Ratio | 0.74 | 0.61 |
| Maximum Drawdown | -19.6% | -50.9% |

The strategy therefore achieved similar long-run growth while exhibiting substantially lower volatility and drawdown in this historical sample.

These results should not be interpreted as evidence of a directly tradable strategy, since transaction costs and other implementation effects are not yet incorporated.

## Robustness

The momentum rule is also tested using alternative lookback periods:

- 6 months
- 9 months
- 12 months
- 18 months

The 12-month specification produced the strongest overall risk-adjusted performance among the tested horizons, although the results vary across specifications.

## Repository

The main analysis is contained in:

`01_momentum_analysis.ipynb`

The notebook contains the complete research workflow, including data preparation, statistical analysis, regression diagnostics, backtesting, risk metrics, and robustness checks.

## Tools

- Python
- pandas
- NumPy
- SciPy
- statsmodels
- Jupyter Notebook

## Limitations and Further Work

Potential extensions include:

- Transaction costs and turnover
- Alternative signal definitions
- Additional asset classes
- Longer historical samples
- Out-of-sample testing
- More realistic portfolio implementation assumptions

## References

Moskowitz, T. J., Ooi, Y. H., & Pedersen, L. H. (2012).  
*Time Series Momentum*. Journal of Financial Economics, 104(2), 228–250.

Hurst, B., Ooi, Y. H., & Pedersen, L. H. (2017).  
*A Century of Evidence on Trend-Following Investing*.
