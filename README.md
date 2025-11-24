This project analyzes the relationship between market sentiment (Fear–Greed Index) and trader performance on Hyperliquid.
The goal is to understand whether market emotions influence profitability, risk, trade frequency, and trader behavior and to build a predictive baseline model for trade profitability.

This assignment was completed as part of the Junior Data Scientist – Trader Behavior Insights hiring process.

Dataset Summary
1. Fear–Greed Index Dataset
Daily sentiment score
Columns: date, timestamp, value, classification
Categories include: Extreme Fear, Fear, Neutral, Greed, Extreme Greed

2. Hyperliquid Historical Trades
Contains detailed real trade-level history:
Account, Coin, Execution Price, Size USD, Side
Timestamp IST, Closed PnL, Fee, Start Position
many more operational features


---- Project Workflow---
The project follows a structured data science workflow:
1. Data Cleaning & Preparation
✔ Parsed timestamps from multiple formats
✔ Converted sentiment timestamps into uniform dates
✔ Cleaned numeric columns (Size USD, Closed PnL, Execution Price)
✔ Created profit_flag target variable
✔ Removed duplicate & invalid records


2. Exploratory Data Analysis (EDA)
Visualizations included:
🔹 Time-series Analysis
Market average PnL vs Sentiment score
Win-rate trends across Fear/Greed phases
🔹 Distribution Plots
Closed PnL distribution
Win-rate per sentiment category
🔹 Heatmaps & Symbol Behavior
Symbol × Sentiment average PnL
Top/bottom performing coins
🔹 Boxplots
PnL shifts across different sentiment regimes


3. Statistical Testing
To compare Fear vs Greed days:
✔ Mann–Whitney U Test
Result: Significant difference between Fear & Greed day PnL
→ Sentiment clearly impacts performance.

✔ Spearman Correlation
Positive correlation between sentiment score and average market win-rate.
→ Higher sentiment → better trader outcomes.

4. Predictive Modeling (Final Model: Logistic Regression)

Only Logistic Regression was used for predictive modeling to avoid leakage and ensure interpretability.
Model Performance
Metric	Score
Accuracy	82%
ROC-AUC	0.978
Loss Recall	1.00
Profit Precision	1.00

Interpretation:
Model perfectly identifies losing trades → strong risk detection
When predicting profitable trades, it is always correct
Excellent for trade filtering / risk management
(This model was chosen as final due to reliability, interpretability, and avoiding data leakage.)

 Key Insights
1. Sentiment drives trader behavior
Greed → higher PnL, higher activity
Fear → larger losses, unstable PnL

2. Logistic regression shows sentiment has predictive power
Higher sentiment score = higher probability of profit

3. Symbol-level analysis reveals non-uniform behavior
Certain symbols perform significantly better during Greed periods.

4. Market PnL strongly correlates with sentiment spikes
→ High sentiment days = more profitable trading environment.


 Business Recommendations
Reduce exposure on Fear days (lower expected PnL).
Increase exposure slightly on Greed days (higher probability of profit).
Use the logistic regression model as a risk filter to avoid high-loss trades.
Incorporate sentiment directly into trading bots or automated strategies.
Build a real-time dashboard showing sentiment, PnL trends & symbol performance.
