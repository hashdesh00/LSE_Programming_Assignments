# Predictive Analysis of Stock Market Performance Using Statistical and Financial Methods

## Overview
This project involves constructing and analyzing portfolios for 10 selected stocks from the S&P500 index over the past 10 years. Using historical return data, portfolios were rebalanced on a rolling window basis to optimize risk and return. The performance was evaluated using Sharpe ratios and AvsAchg metrics.

## Objective
The goal was to build an optimized portfolio using mean-variance analysis, compute key performance metrics, and evaluate the impact of various tuning parameters.

## Methodology (Summary)
- Downloaded daily closing prices for the 10 stocks and the S&P500 index.
- Constructed and rebalanced a portfolio on a rolling window basis, adjusting weights every `I` trading days using historical return data.
- Evaluated portfolio performance using the annualized Sharpe ratio and average sum absolute changes in portfolio weights (AvsAchg).

## Key Sections and Concepts

### [Question 1: Data Preprocessing and Initial Setup](./question1.md)
- **Key Concepts**: 
  - Data cleaning and handling missing values.
  - Log prices and return calculations.
  - Calculation of covariance matrix and condition numbers.

### [Question 2: Constructing a Portfolio on a Rolling Window Basis](./question2.md)
- **Key Concepts**:
  - Rolling mean returns and rebalancing portfolio weights.
  - Quadratic programming for weight optimization.
  - Covariance matrix regularization to handle volatility and instability.

### [Question 3: Sensitivity Analysis and Tuning Parameters](./question3.md)
- **Key Concepts**:
  - Sensitivity analysis of key parameters: `t0`, `D`, `I`, and `x`.
  - Sharpe ratio and AvsAchg trade-off evaluation.
  - Optimization of parameter sets for better risk-adjusted returns and portfolio stability.

### [Question 4: Performance Evaluation and Comparison](./question4.md)
- **Key Concepts**:
  - Final comparison of different strategies using performance metrics.
  - Selection of the best-performing parameter set.

## Key Results
- The best-performing portfolio achieved a Sharpe ratio of 0.74.
- The optimal balance between Sharpe ratio and AvsAchg was achieved by using parameter set `X`.

## How to Run the Code
You can run the rolling window investment strategy by executing the R script with the following parameters:
```r
result <- investment_strategy(x = 0.01, t0 = 1, D = 252, I = 21)

