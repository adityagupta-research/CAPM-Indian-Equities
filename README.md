# CAPM Analysis of Indian Equities

A Python-based empirical analysis of the Capital Asset Pricing Model (CAPM) using daily returns for four NSE-listed companies and the NIFTY 50 as the market proxy.

## Project objective

The project estimates:

- **Beta** - sensitivity of each stock's returns to the NIFTY 50
- **CAPM expected return**
- **Annualized average return**
- **Difference between annualized average return and CAPM-implied return**
- **Security Market Line (SML)**

The goal is to connect the theoretical CAPM framework with real market data and implement the calculations in Python.

## Sample

| Security | Ticker |
|---|---|
| HDFC Bank | `HDFCBANK.NS` |
| TCS | `TCS.NS` |
| Reliance Industries | `RELIANCE.NS` |
| Infosys | `INFY.NS` |
| NIFTY 50 | `^NSEI` |

**Period:** January 2020 – December 2024  
**Frequency:** Daily  
**Risk-free rate:** 7% per annum  
**Annualization:** 252 trading days

## Methodology

Daily returns are calculated from adjusted prices:

`R_t = P_t / P_(t-1) - 1`

Beta is estimated as:

`Beta_i = Cov(R_i, R_m) / Var(R_m)`

CAPM expected return:

`E(R_i) = R_f + Beta_i × (E(R_m) - R_f)`

For this project, `E(R_m)` and each stock's annualized average return are estimated as the mean daily return multiplied by 252.

The project also plots the Security Market Line to visualize the CAPM relationship between Beta and expected return.

## Results

The original analysis produced the following results:

| Stock | Beta | CAPM Expected Return | Annualized Average Return | Return Difference |
|---|---:|---:|---:|---:|
| HDFC Bank | 1.08 | 15.82% | 10.5% | -5.33% |
| TCS | 0.75 | 13.11% | 17.90% | +4.78% |
| Reliance Industries | 1.11 | 16.06% | 16.36% | 0.30% |
| Infosys | 0.89 | 14.27% | 25.51% | +11.24% |

### Interpretation

The results show that Beta and realized returns are not mechanically linked. For example, TCS had a lower Beta than HDFC Bank and Reliance in the sample but a higher annualized average return.

A positive return difference indicates that the observed annualized average return was above the CAPM-implied return for this sample. It is **not** formal Jensen's alpha because this project does not estimate a regression intercept.

## Project structure

```text
CAPM_Indian_Equities/
├── CAPM_Analysis_Indian_Equities.ipynb
├── README.md
├── requirements.txt
└── .gitignore
```

## How to run

Clone the repository and install the dependencies:

```bash
pip install -r requirements.txt
```

Then open:

```bash
jupyter notebook CAPM_Analysis_Indian_Equities.ipynb
```

The notebook downloads the historical market data directly through `yfinance`, so no local CSV dataset is required.

## Limitations

This is an introductory empirical CAPM project. It does not attempt to establish that CAPM is the best asset-pricing model.

Possible extensions include:

- rolling Beta estimation
- formal CAPM regression
- statistical significance tests
- sub-period analysis
- sector-level comparisons
- larger stock universe
- Fama-French factor comparison
- transaction-cost and portfolio-level analysis

## Data source

Historical price data is retrieved from Yahoo Finance using the `yfinance` Python package.

**Disclaimer:** Educational/research project only. Nothing in this repository is investment advice.
