# Sensitivity Analysis: Portfolio Selection Strategy

## Objective
This analysis evaluates the performance of a rolling-window portfolio strategy by systematically varying key parameters. 
The goal is to optimize the portfolio’s Sharpe ratio while minimizing the average sum absolute changes in portfolio weights (AvsAchg). 
The parameters of interest include:
- **t0**: Start time of the investment period
- **D**: Rolling window length for computing historical mean returns and covariances
- **I**: Rebalancing interval for adjusting portfolio weights
- **x**: Scaling factor influencing the target return in quadratic optimization

---

## Methodology

### 1. Parameter Definitions
We systematically varied the following parameters within defined ranges to evaluate their impact on portfolio performance:
- **t0**: The start point for the investment, chosen to reflect an appropriate lead-in period for the historical data.
- **D**: The window length for computing rolling statistics, with a trade-off between stability (longer `D`) 
and responsiveness (shorter `D`).
- **I**: The interval for rebalancing portfolio weights, balancing transaction costs and capturing market opportunities.
- **x**: A scaling factor used in the optimization for the portfolio's target return, balancing the risk-return trade-off.

### 2. Performance Metrics
Two key metrics were used to evaluate the portfolio strategy:
- **Sharpe Ratio**: This measures the risk-adjusted return of the portfolio and is calculated as:

`Sharpe Ratio = (√252 × Average Daily Return) / (Standard Deviation of Daily Returns)`

- **AvsAchg (Average Sum Absolute Changes in Weights)**: This metric measures the stability of portfolio weights:

`AvsAchg = (1 / Total number of periods) × Σ | wt+1 - wt |`


### 3. Sensitivity Analysis Approach
- The sensitivity analysis involved varying one parameter while holding the others constant. 
This allowed us to observe how changes in each parameter affected the portfolio's Sharpe ratio and AvsAchg.
- The baseline parameter set used was: `t0 = 1000`, `D = 90`, `I = 90`, and `x = 1`.
- Performance metrics were calculated for each parameter combination, and the results were stored for comparison.

---

## Results

### 1. Sharpe Ratio Insights
- **Starting Point (`t0`)**: The Sharpe ratio was highly sensitive to the start time of the investment period.
Certain start times led to drastically different outcomes, emphasizing the importance of selecting an appropriate lead-in period.
- **Window Length (`D`)**: Longer windows (e.g., `D > 180`) reduced the Sharpe ratio due to a lag in responding to market changes. 
Shorter windows were more responsive but introduced higher volatility in the portfolio.
- **Rebalancing Interval (`I`)**: The rebalancing interval had minimal impact on the Sharpe ratio. 
This suggests that less frequent rebalancing may still achieve similar risk-adjusted returns, helping to reduce transaction costs.
- **Scaling Factor (`x`)**: The impact of `x` on the Sharpe ratio was minor, 
suggesting that the target return scaling did not have a significant effect within the tested range.

### 2. AvsAchg Insights
- **Stability of Portfolio Weights**: Lower AvsAchg values were achieved when the rebalancing interval (`I`) and window length (`D`) 
were aligned. This suggests that matching the frequency of rebalancing with the length of the data window improves portfolio stability.
- **Transaction Costs**: A smaller AvsAchg implies lower transaction costs, as fewer and smaller adjustments were made to the portfolio weights.
This is critical in long-term investment strategies where transaction costs can erode returns.

### 3. Optimal Parameter Selection
After performing the sensitivity analysis, the optimal parameter set was determined to be:
- `t0 = 500`
- `D = 60`
- `I = 70`
- `x = 1.2`

This parameter combination resulted in a Sharpe ratio of **0.74** and an AvsAchg of **9.9789**, 
achieving a good balance between risk-adjusted returns and portfolio stability.

---

## Key Takeaways
- **Sharpe Ratio Optimization**: The starting time of the investment and the window length for rolling statistics had the most significant 
impact on the Sharpe ratio. Shorter windows provided more timely responses to market conditions but introduced more volatility.
- **Portfolio Stability**: The stability of portfolio weights, as measured by AvsAchg, was improved when the rebalancing interval and
window length were closely aligned. This led to fewer and smaller portfolio adjustments, reducing transaction costs.
- **Balanced Strategy**: The selected parameter combination (`t0 = 500`, `D = 60`, `I = 70`, `x = 1.2`) 
provided the best trade-off between maximizing the Sharpe ratio and minimizing portfolio rebalancing.

---

## Code Reference
For a detailed implementation of the sensitivity analysis and the portfolio strategy, 
please refer to the following code files in this repository:
- [Portfolio Strategy Code](./code/portfolio_strategy.R)
- [Sensitivity Analysis Code](./code/sensitivity_analysis.R)

---

## Conclusion
This sensitivity analysis highlights the importance of carefully tuning key parameters in a portfolio selection strategy 
to achieve the optimal balance between risk-adjusted returns and portfolio stability. 
By identifying the best parameter set, we can implement a robust investment strategy that adapts to varying market conditions
while minimizing transaction costs.
