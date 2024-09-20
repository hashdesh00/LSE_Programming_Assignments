# Question 4: Performance Evaluation and Comparison

### Objective:
The goal is to identify the optimal parameter setting that achieves the best balance between maximizing the Sharpe ratio and minimizing Avs Achg. This approach ensures better risk-adjusted returns and efficient portfolio rebalancing.

---

### 1. Optimization Criteria:
To find the optimal parameter settings, we defined our optimization criteria based on a trade-off between a higher Sharpe ratio and a lower Avs Achg. The parameters were optimized to improve risk-adjusted returns while minimizing transaction costs from frequent portfolio rebalancing.

We sorted the results by descending Sharpe ratios and ascending Avs Achg, ensuring that the top results in the table reflect the parameter inputs that satisfy our optimization goals.

---

### 2. Optimal Parameter Combination:
The resulting optimal parameter combination was found to be:
- **t0 = 500**
- **D = 60**
- **I = 70**
- **x = 1.2**

This combination produced:
- **Sharpe Ratio**: 0.74
- **Avs Achg**: 9.9789

This parameter set achieved both a large Sharpe ratio and a relatively small Avs Achg, indicating an efficient balance between risk-adjusted returns and portfolio stability.

---

### 3. Strategy Insights:
- **D (Trading Window)**: The trading window is used to determine portfolio weights. The optimal values of `D` and `I` were found to be the same or very close, ensuring that the strategy's responsiveness aligns with the frequency of rebalancing. This led to better investment decisions and minimized unnecessary portfolio adjustments.
  
- **I (Rebalance Period)**: The frequency of rebalancing should consider both market conditions and transaction costs. Rebalancing too frequently may lead to higher costs, while too infrequent rebalancing may miss market opportunities. By aligning `D` and `I`, we ensured a more responsive and stable strategy.

- **Tuning `t0`**: We varied the start time `t0` during backtesting to evaluate the strategy across different market phases (bull, bear, and high volatility). The flexibility of `t0` allowed us to maximize our performance metrics in diverse market conditions.

---

### 4. Parameter Impact on Avs Achg:
- **x Parameter**: When `x` was increased beyond 2.5, the Avs Achg became larger, indicating that more aggressive portfolio adjustments were required. This can increase transaction costs and is generally undesirable in long-term strategies. Keeping `x` close to 1 resulted in a more reasonable target return and minimized unnecessary portfolio adjustments.

- **D and I**: The alignment of `D` (trading window) and `I` (rebalance period) led to improved Sharpe ratios and lower Avs Achg. This suggests that keeping these parameters closely aligned provides the best balance between responsiveness to market conditions and portfolio stability. `I` had a significant impact on the Avs Achg, with longer periods reducing the frequency of costly portfolio adjustments.

---

### 5. Conclusion:
The optimal portfolio strategy is to keep `D` and `I` closely aligned, with `x` set near 1 to minimize aggressive portfolio adjustments. The strategy must be flexible and adaptable to changing market conditions and investment goals.

By varying the parameters and testing in different market scenarios, we were able to optimize our inputs and strike a balance between maximizing the Sharpe ratio and minimizing Avs Achg. This ensured better risk-adjusted returns and more efficient portfolio management.

---

