## Question 2: Constructing a Portfolio on a Rolling Window Basis

### Objective:
The objective is to create a portfolio consisting of 10 selected stocks, adjusting the portfolio weights every `I` trading days using historical return data over the past `D` days. The strategy seeks to maximize risk-adjusted returns while maintaining stable portfolio weights and avoiding investment in any risk-free assets.

---

### 1. Initial Setup:
The portfolio is initialized at time `t0`, with an equal allocation of weights to all the selected stocks. The portfolio weights are then adjusted every `I` trading days using stock returns from the previous `D` days. These weights are optimized to achieve a target portfolio return while minimizing portfolio variance.

---

### 2. Calculating Rolling Mean Returns:
- The rolling mean return for each stock is computed using the past `D` days of return data. This provides a time-windowed estimate of the average return for each stock in the portfolio.
- The rolling mean returns serve as the basis for adjusting the portfolio weights at every rebalancing point.

---

### 3. Weight Adjustments and Optimization:
- At every rebalancing point `t = t0 + nI`, we adjust the portfolio weights based on the historical returns over the past `D` trading days. 
- The weights are optimized by solving a quadratic optimization problem with two key constraints:
  1. The sum of the portfolio weights must equal 1.
  2. The target return must be achieved using the optimized weights.
- Here we utilise the two fund theorem from portfolio allocation theory. 
---

### 4. Covariance Matrix Regularization:
- The covariance matrix of the asset returns over the past `D` days is used in the optimization process. A small shrinkage term (epsilon) is applied to the covariance matrix to ensure it remains positive semi-definite and stable.
- This regularization step ensures the optimization is not overly sensitive to noise in the covariance estimates, especially during periods of market volatility.

---

### 5. Execution of the Investment Strategy:
- The portfolio is rebalanced every `I` trading days. For each day within the `I`-day period, the weights remain constant, and the portfolio returns are calculated based on the stock prices for that day.
- The portfolio return on each day is the weighted sum of the returns of the individual stocks.

---

### 6. Performance Metrics:
- **Annualized Sharpe Ratio**: This ratio measures the risk-adjusted return of the portfolio over the entire investment period. It is calculated by annualizing the portfolio's daily returns, adjusted for volatility.
  
- **Average Sum of Absolute Changes in Weights (AvsAchg)**: This metric measures the stability of portfolio weights. It calculates the average sum of absolute changes in the weights between rebalancing periods. A lower AvsAchg indicates more stable weights, leading to lower transaction costs.

---

### 7. Code Reference:
The complete code to implement the rolling window portfolio strategy, including the calculation of the Sharpe ratio and AvsAchg, can be found in the following code file:
- [Rolling Window Portfolio Strategy Code](./code/portfolio_strategy.R)

This function allows for adjusting the parameters `t0`, `D`, `I`, and `x` to explore how different values affect the portfolio's performance.

---

### 8. Conclusion:
The rolling window portfolio construction strategy effectively adjusts weights based on historical return data, allowing the portfolio to adapt to changing market conditions. By optimizing the parameters, the strategy balances risk-adjusted returns with portfolio stability. This framework is essential for dynamic portfolio management in volatile market environments.

---

### Next Steps:
For further analysis and parameter tuning, see **Question 3** on sensitivity analysis, where different parameter combinations are systematically explored to optimize portfolio performance.

---

