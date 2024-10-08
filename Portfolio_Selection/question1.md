# Data Preprocessing and Methodology for Stock Price Analysis

This section details the data preprocessing steps and methodology used for Question 1 of the stock market analysis project. 
The objective was to download daily closing prices of 10 selected stocks from the S&P500,
calculate their log prices, handle any missing values,
and compute the condition number of the covariance matrix using different time windows.

## Question 1: Portfolio Construction and Data Preprocessing 
## 1. Stock Selection and Data Download

The selected stocks for this analysis are Apple (AAPL), Microsoft (MSFT), Amazon (AMZN), Nvidia (NVDA), Tesla (TSLA),
Meta (META), United Health Group (UNH), Exxon Mobil (XOM), JPMorgan (JPM), and Johnson & Johnson (JNJ).

To download the daily closing prices of the 10 selected stocks, 
I used the `getSymbols` function from the `quantmod` package in R. The data spans the past 10 years, from January 2013 to January 2023.

### Code:
```r
library(quantmod)

symbols <- c("AAPL", "MSFT", "AMZN", "NVDA", "TSLA", "META", "UNH", "XOM", "JPM", "JNJ")
getSymbols(symbols, src = "yahoo", from = "2013-01-01", to = "2023-01-01")
```
## 2. Log Prices Calculation

Log prices were calculated for each stock to stabilize variance and convert multiplicative relationships into additive ones. 
This transformation helps in better understanding the price dynamics over time.

### Code:
```r
log_prices <- lapply(symbols, function(sym) log(Cl(get(sym))))
```
## 4. Plotting Log Prices

The log prices of the 10 selected stocks were plotted to visualize the trends over the past 10 years. 
Each stock displayed an upward trend, with some notable dips during major events like the COVID-19 pandemic.

### Code:
```r
library(ggplot2)

# Combine the log prices into a data frame for plotting
log_prices_df <- do.call(merge, log_prices)

# Plot the log prices
plot.zoo(log_prices_df, main = "Log Prices of Selected Stocks (2013-2023)", ylab = "Log Prices", xlab = "Date")

```
## 5. Covariance Matrix and Condition Number Calculation

To assess the stability of the covariance matrix,
I calculated the condition number for different time periods: 10 years, 5 years, and 1 year.
The condition number provides insight into the potential instability in the covariance matrix estimates.

### Code:
```r
# Calculate log returns
log_returns <- diff(log_prices_df)
log_returns <- na.omit(log_returns)

# Covariance matrix for the 10-year period
cov_matrix <- cov(log_returns)

# Calculate condition number using SVD
svd_result <- svd(cov_matrix)
condition_number <- max(svd_result$d) / min(svd_result$d)
condition_number
```
## 6. Insights from the Data

- Tesla (TSLA) exhibited exceptional growth over the 10-year period, especially post-2019.
- The COVID-19 pandemic negatively impacted all stocks, though Nvidia (NVDA) was the least affected.
- Economic downturns in 2022 caused a dip in prices for most companies, 
with United Health Group (UNH) and Exxon Mobil (XOM) showing marginal increases.



