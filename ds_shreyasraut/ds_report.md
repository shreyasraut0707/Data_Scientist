# Data Science Report

## Trader Behavior Analysis: Fear vs Greed Market Sentiment

---

**Candidate:** Shreyas  
**Position:** Junior Data Scientist - Trader Behavior Insights  
**Date:** November 6, 2025  
**Assignment:** Web3 Trading Team - Hyperliquid Analysis

---

## Executive Summary

This report presents a comprehensive analysis of cryptocurrency trader performance across different market sentiment periods. Using over 211,000 historical trades from Hyperliquid combined with Bitcoin Fear & Greed Index data, we examined how market sentiment (Fear vs Greed) impacts trading profitability, win rates, risk profiles, and trading behavior.

**Key Question:** Do traders perform better during Fear or Greed market conditions?

**Answer:** Greed periods demonstrate marginally superior performance (+9.5% higher average PnL and +1.24% better win rate), but the difference is **not statistically significant** (p=0.32). This suggests market sentiment alone is not a robust predictor of trading success, and other factors like risk management and execution quality are more critical.

---

## 1. Objective

The primary objective of this analysis is to:

- **Explore** the relationship between trader performance and market sentiment
- **Compare** profitability metrics during Fear vs Greed periods
- **Identify** hidden patterns that can inform smarter trading strategies
- **Provide** data-driven recommendations for optimizing trading performance

---

## 2. Data Description

### 2.1 Datasets Used

#### Fear & Greed Index Dataset

- **Source:** Bitcoin Market Sentiment Index
- **Time Period:** February 2018 - December 2024
- **Records:** 2,646 daily sentiment readings
- **Classifications:** Extreme Fear, Fear, Neutral, Greed, Extreme Greed

#### Historical Trader Data

- **Source:** Hyperliquid Trading Platform
- **Records:** 211,226 trades
- **Key Metrics:** Account, Symbol, Execution Price, Size (USD), Side (Buy/Sell), Closed PnL, Leverage, Timestamp
- **Data Quality:** High-quality structured data with minimal missing values

### 2.2 Data Preparation

**Cleaning Steps:**

1. Converted all timestamps to standardized datetime format
2. Removed trades with missing PnL or date information (8 records removed)
3. Merged datasets on date field using inner join
4. Created binary sentiment categories (Fear = Extreme Fear + Fear; Greed = Extreme Greed + Greed)
5. Validated data consistency and removed duplicates

**Final Merged Dataset:** 211,218 trades with matched sentiment labels (173,532 trades analyzed after excluding Neutral sentiment)

---

## 3. Methodology

### 3.1 Analysis Framework

Our analysis follows a systematic approach:

1. **Exploratory Data Analysis (EDA)**

   - Distribution analysis of sentiment classifications
   - Trading volume patterns
   - PnL distribution characteristics

2. **Comparative Analysis**

   - Group trades by sentiment (Fear vs Greed)
   - Calculate performance metrics for each group
   - Compare averages, medians, and distributions

3. **Statistical Testing**

   - Independent t-test to determine statistical significance
   - P-value threshold: 0.05 (α = 5%)

4. **Risk Assessment**

   - Volatility comparison using standard deviation
   - Distribution analysis using boxplots and violin plots

5. **Behavioral Analysis**
   - Buy vs Sell performance by sentiment
   - Trade volume and size patterns
   - Time-series trend analysis

### 3.2 Key Metrics

- **Average PnL:** Mean profit/loss per trade
- **Total PnL:** Cumulative profit/loss
- **Win Rate:** Percentage of profitable trades (PnL > 0)
- **Volatility:** Standard deviation of PnL (risk measure)
- **Trade Volume:** Number of trades and total USD value
- **Trade Size:** Average USD size per trade

---

## 4. Key Findings

### 4.1 Profitability Analysis

**Performance Comparison:**

| Metric      | Fear Periods  | Greed Periods | Winner | Difference |
| ----------- | ------------- | ------------- | ------ | ---------- |
| Average PnL | $49.21        | $53.88        | Greed  | +9.5%      |
| Total PnL   | $4,096,265.69 | $4,865,300.58 | Greed  | +18.8%     |
| Median PnL  | $0.00         | $0.00         | Tie    | 0%         |

**Key Observation:**

Greed periods demonstrate superior profitability with an average PnL of $53.88 compared to $49.21 during Fear periods, representing a 9.5% performance advantage. The total PnL during Greed periods ($4.87M) exceeds Fear periods ($4.10M) by 18.8%. However, the median PnL is $0 for both sentiment states, indicating that the majority of trades close at break-even, with profitability driven by outlier winning trades.

**Chart Reference:** See `outputs/pnl_by_sentiment.png`

---

### 4.2 Win Rate Analysis

**Win Rate Comparison:**

| Sentiment | Win Rate | Winning Trades | Losing Trades | Neutral Trades | Total Trades |
| --------- | -------- | -------------- | ------------- | -------------- | ------------ |
| Fear      | 40.79%   | 33,957         | 7,212         | 42,068         | 83,237       |
| Greed     | 42.03%   | 37,960         | 8,264         | 44,071         | 90,295       |

**Key Observation:**

Win rates during Greed periods (42.03%) exceed those during Fear periods (40.79%) by 1.24 percentage points. While this difference appears modest, it represents approximately 3% relative improvement in winning probability. Notably, over 50% of all trades close at break-even ($0 PnL) across both sentiment periods, suggesting many traders use tight stop-losses or close positions quickly to minimize losses.

**Chart Reference:** See `outputs/win_rate_analysis.png`

---

### 4.3 Statistical Significance

**T-Test Results:**

- **T-Statistic:** -0.9881
- **P-Value:** 0.323117
- **Significance Level:** α = 0.05
- **Result:** NOT STATISTICALLY SIGNIFICANT

**Interpretation:**

The independent samples t-test yields a p-value of 0.323, which is substantially higher than the conventional significance threshold of 0.05. This indicates that the observed differences in average PnL between Fear and Greed periods could reasonably be attributed to random chance rather than a true systematic effect.

**Critical Implication:** Market sentiment alone is **not a robust predictor** of trading success. While Greed periods show marginally better performance, traders cannot rely on sentiment as a primary signal for position entry or risk allocation.

---

### 4.4 Risk & Volatility Analysis

**Volatility Comparison:**

| Sentiment | Volatility (Std Dev) | Higher Risk  |
| --------- | -------------------- | ------------ |
| Fear      | $990.88              | Fear (+1.4%) |
| Greed     | $976.96              | -            |

**PnL Distribution Characteristics:**

- **Fear Periods:** Higher standard deviation indicates slightly elevated risk exposure
- **Greed Periods:** Marginally lower volatility suggests more consistent outcomes
- **Distribution Shape:** Both periods exhibit similar long-tailed distributions with outliers

**Key Observation:**

Fear periods exhibit 1.4% higher volatility ($990.88 vs $976.96), but the difference is minimal. Both sentiment periods maintain similar risk profiles, indicating that market structure and trader behavior remain relatively stable regardless of sentiment. This suggests position sizing and risk management protocols should be consistent across sentiment regimes rather than sentiment-dependent.

**Chart Reference:** See `outputs/pnl_distribution_by_sentiment.png`

---

### 4.5 Trading Volume Analysis

**Volume Metrics:**

| Sentiment | Total Trades | Percentage | Average Daily Volume |
| --------- | ------------ | ---------- | -------------------- |
| Fear      | 83,237       | 47.96%     | ~126 trades/day      |
| Greed     | 90,295       | 52.04%     | ~136 trades/day      |

**Key Observation:**

Trading activity is 8.5% higher during Greed periods (90,295 trades) compared to Fear periods (83,237 trades). This aligns with behavioral finance theory: traders are more active and willing to enter positions when market sentiment is positive. The distribution is nearly balanced (48% Fear, 52% Greed), indicating the dataset covers both market conditions adequately.

**Chart Reference:** See `outputs/volume_analysis.png`

---

### 4.6 Buy vs Sell Performance

**Trading Side Analysis:**

| Side | Fear Avg PnL | Greed Avg PnL | Better Sentiment |
| ---- | ------------ | ------------- | ---------------- |
| Buy  | $49.85       | $54.12        | Greed (+8.6%)    |
| Sell | $48.32       | $53.52        | Greed (+10.8%)   |

**Key Observation:**

Both Buy and Sell trades perform better during Greed periods, with Sell trades showing slightly larger performance improvement (+10.8% vs +8.6%). This suggests the sentiment effect is directionally agnostic—positive sentiment benefits both long and short positions, possibly due to increased liquidity, tighter spreads, or improved market structure during bullish conditions.

**Chart Reference:** See `outputs/buy_sell_sentiment_analysis.png`

---

### 4.7 Time-Series Trends

**Cumulative PnL Over Time:**

The cumulative PnL chart reveals:

- **Greed periods:** Generally steeper upward trajectories with sustained profitability
- **Fear periods:** More volatile paths with frequent drawdowns and recoveries
- **Overall trend:** Both sentiment types contribute positively to cumulative returns over the full time period

**Key Observation:**

While both Fear and Greed periods contribute to overall profitability, Greed periods show more consistent upward momentum. Fear periods exhibit higher volatility in cumulative returns, with sharp drawdowns followed by recoveries. This supports the earlier finding that Fear periods carry slightly elevated risk.

**Chart Reference:** See `outputs/cumulative_pnl_over_time.png`

---

## 5. Strategic Insights & Recommendations

### Insight 1: Sentiment as a Secondary Filter

**Finding:** Greed periods show 9.5% better average PnL, but the difference is not statistically significant.

**Recommendation:**

- Use market sentiment as a **secondary filtering criterion**, not a primary signal
- Do not alter core trading strategies based solely on Fear/Greed classifications
- Focus on trade setup quality, entry/exit execution, and risk management

### Insight 2: Consistent Risk Management Across Regimes

**Finding:** Both Fear and Greed periods exhibit similar volatility (~$980 std dev) and risk profiles.

**Recommendation:**

- Maintain **consistent position sizing** regardless of sentiment
- Do not increase leverage during Greed periods assuming lower risk
- Use standardized stop-loss and take-profit protocols across all market conditions

### Insight 3: Activity Increases in Greed

**Finding:** Trading volume is 8.5% higher during Greed periods.

**Recommendation:**

- Be aware of **increased market participation** during bullish sentiment
- Higher volume may lead to better liquidity but also increased competition
- Consider wider stops during high-activity periods to avoid premature exits

### Insight 4: Execution Quality Matters Most

**Finding:** Win rates are nearly identical (40.79% vs 42.03%), and median PnL is $0 for both sentiments.

**Recommendation:**

- Prioritize **trade execution quality** over sentiment timing
- Focus on entry precision, slippage reduction, and optimal exit timing
- Develop robust position management skills (scaling in/out, partial profit-taking)

### Insight 5: Avoid Sentiment-Driven Overtrading

**Finding:** Traders are more active during Greed periods, but performance improvement is marginal.

**Recommendation:**

- Avoid **overtrading** during positive sentiment periods
- Maintain disciplined trade selection criteria
- Remember: more trades ≠ more profit if edge remains constant

---

## 6. Limitations & Future Work

### 6.1 Limitations

1. **Sentiment Lag:** Fear/Greed Index is calculated daily, but trades occur intraday. Intraday sentiment shifts are not captured.

2. **Account-Level Anonymity:** Dataset does not reveal account-level details, preventing analysis of individual trader skill vs luck.

3. **Market Conditions:** Dataset spans 2018-2024, including bull, bear, and sideways markets. Macro conditions may confound sentiment effects.

4. **Leverage Impact:** While leverage data is available, this analysis did not deeply explore leverage interactions with sentiment.

5. **External Factors:** News events, regulatory changes, and macroeconomic factors are not controlled for.

### 6.2 Future Work Opportunities

1. **Machine Learning Models:** Build predictive models incorporating sentiment, price action, volume, and volatility.

2. **Account Clustering:** Use unsupervised learning to identify trader archetypes (scalpers, swing traders, etc.) and analyze sentiment effects per group.

3. **Intraday Analysis:** Incorporate intraday sentiment data (if available) to capture granular behavioral patterns.

4. **Multi-Asset Analysis:** Extend analysis to other cryptocurrencies (ETH, SOL, etc.) to test sentiment generalization.

5. **Leverage Optimization:** Develop sentiment-adjusted leverage recommendations based on risk tolerance.

6. **Alternative Sentiment Sources:** Integrate social media sentiment (Twitter, Reddit) and on-chain metrics for richer analysis.

---

## 7. Visualizations Summary

All visualizations are saved in the `outputs/` folder:

1. **sentiment_distribution.png** - Distribution of Fear/Greed classifications in trade data
2. **buy_sell_distribution.png** - Proportion of Buy vs Sell trades (nearly 50/50 split)
3. **pnl_distribution.png** - Overall PnL distribution showing long-tailed pattern
4. **pnl_by_sentiment.png** - Average and Total PnL comparison (Fear vs Greed)
5. **win_rate_analysis.png** - Win rate comparison with winning/losing trade breakdown
6. **volume_analysis.png** - Trading volume and trade count by sentiment
7. **pnl_distribution_by_sentiment.png** - Risk profile comparison (Boxplot & Violin)
8. **buy_sell_sentiment_analysis.png** - Buy/Sell performance across sentiments
9. **cumulative_pnl_over_time.png** - Time-series cumulative PnL trends

---

## 8. Conclusion

This analysis of 211,218 trades across 6+ years of Bitcoin Fear & Greed Index data reveals that **market sentiment has a marginal but not statistically significant impact on trading performance**. While Greed periods show 9.5% better average PnL and 1.24% higher win rates, the p-value of 0.323 indicates these differences could be due to random variation.

**Key Takeaway:** Successful trading depends more on **execution quality, risk management, and position sizing** than on timing entries based on sentiment alone. Traders should view sentiment as contextual information rather than a primary decision factor.

**Practical Application:**

- Maintain disciplined trading strategies across all sentiment regimes
- Use consistent risk management protocols
- Focus on trade setup quality over sentiment timing
- Avoid overtrading during Greed periods
- Prioritize skill development in execution and risk management

The Web3 trading ecosystem demands data-driven decision-making, and this analysis provides a rigorous foundation for understanding the limited predictive value of aggregate market sentiment on individual trade outcomes.

---

## 9. Technical Appendix

### 9.1 Data Processing Pipeline

```
1. Load Fear/Greed Index (2,646 days) and Historical Trades (211,226 records)
2. Clean timestamps and convert to datetime format
3. Extract date from trader timestamps for merging
4. Remove records with missing PnL or dates (8 records)
5. Merge datasets on date using inner join → 211,218 matched trades
6. Create binary sentiment: Fear (Extreme Fear + Fear), Greed (Extreme Greed + Greed)
7. Exclude Neutral sentiment → 173,532 trades for analysis
8. Calculate metrics: avg PnL, win rate, volatility, volume by sentiment
9. Perform independent t-test for statistical significance
10. Generate 9 visualizations and export summary CSV
```

### 9.2 Tools & Technologies

- **Python 3.11.9**
- **Libraries:** pandas 2.3.3, numpy 2.3.4, matplotlib 3.10.7, seaborn 0.13.2, scipy 1.15.2
- **Environment:** Jupyter Notebook / Google Colab
- **Visualization:** Matplotlib & Seaborn (300 DPI PNG outputs)
- **Statistical Testing:** SciPy stats.ttest_ind()

### 9.3 Reproducibility

All code is available in:

- `notebook_1.ipynb` - Data loading, cleaning, EDA
- `notebook_2.ipynb` - Sentiment analysis, statistical testing, insights
- `run_analysis.py` - Combined execution script

Execution time: ~5 minutes on standard hardware

---

## 10. References & Data Sources

1. **Bitcoin Fear & Greed Index**

   - Source: Alternative.me (via provided dataset)
   - Methodology: Composite index of market volatility, momentum, social media, surveys, and dominance

2. **Hyperliquid Historical Trader Data**

   - Source: Hyperliquid DEX trading platform
   - Coverage: Multi-year historical trade execution data

3. **Statistical Methods**
   - Welch's t-test (independent samples, unequal variances assumed)
   - Significance level: α = 0.05

---

**Report Prepared By:** Shreyas  
**Date:** November 6, 2025  
**Contact:** [Available upon request]

---

_This report was prepared as part of the Junior Data Scientist hiring process for the Web3 Trading Team. All analysis is based on historical data and should not be construed as financial advice._
