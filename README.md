# Time-Series Momentum in the S&P 500

> **Work in progress** — an independent quantitative finance research project.

## Overview

This project investigates whether past market performance contains information about subsequent returns in the S&P 500.

The main research question is:

**If the S&P 500 has a positive return over the previous 12 months, is its return over the following 3 months more likely to be positive?**

The project is inspired by the time-series momentum literature and is being developed as an empirical study of momentum signals, their statistical significance, and their potential use in systematic trading.

## Data

The analysis uses historical daily data for the **S&P 500 Total Return Index**, which includes the reinvestment of dividends.

Daily observations are converted to month-end frequency for the main analysis.

## Methodology

The current research pipeline includes:

- Data collection and cleaning
- Conversion from daily to monthly observations
- Calculation of trailing 12-month returns
- Calculation of forward 3-month returns
- Exploratory analysis of the relationship between past and future returns

Planned extensions include:

- Statistical hypothesis testing
- Signal construction
- Strategy backtesting
- Performance and risk evaluation
- Robustness checks across alternative lookback and holding periods

## Tools

- Python
- pandas
- NumPy
- Jupyter Notebook

## Status

The project is currently under active development. Results and methodology will be updated as the research progresses.

## References

Moskowitz, T. J., Ooi, Y. H., & Pedersen, L. H. (2012). *Time Series Momentum*. Journal of Financial Economics, 104(2), 228–250.
