
##  Market Sentiment & Trader Behavior Insights

###  Project Overview
This project explores how **market sentiment**—represented by the *Fear–Greed Index*—influences **trader performance and behavior**.  
By combining **Bitcoin Market Sentiment data** with **Historical Trader Data from Hyperliquid**, the goal was to uncover how emotions like *fear* and *greed* impact trading outcomes such as profits and trade sizes.  
Machine Learning models were used to predict trader performance and identify patterns that can guide smarter, emotion-aware trading strategies in the Web3 space.



###  1. Dataset Overview
Two datasets were used and later merged:
1. **Bitcoin Market Sentiment Dataset** – Columns: `Date`, `Classification (Fear/Greed)`, `sentiment_score`  
2. **Trader Data from Hyperliquid** – Columns: `Account`, `Coin`, `Execution Price`, `Size Tokens`, `Size USD`, `Side`, `Closed PnL`, `Direction`, `Leverage`, `trade_date`, etc.

After merging and cleaning, the final dataset had **211,224 rows** and **12 columns**, including:
- **Categorical Features:** Account, Coin, Side, Direction, Classification  
- **Numerical Features:** Execution Price, Size Tokens, Size USD, Closed PnL, Sentiment Score  
- **Dates:** trade_date, sentiment_date  



###  2. Exploratory Data Analysis (EDA)

####  Univariate Insights
- Most trades were concentrated in a few major coins.  
- *Closed PnL* distribution was right-skewed — indicating more small losses than large profits.  
- Sentiment scores showed balanced distribution between *Fear* and *Greed*.  

####  Bivariate Insights
- *Closed PnL* increased notably during **Greed** phases.  
- A positive correlation was seen between **Sentiment Score** and **Closed PnL** — traders performed better when the market was optimistic.  
- The side of the trade (Buy/Sell) also affected profitability patterns.  

####  Multivariate Insights
- A 3D relationship among *Trade Size (USD)*, *Execution Price*, and *Closed PnL* showed clear clusters for profitable vs. loss-making trades.  
- Correlation heatmaps revealed that **Sentiment Score**, **Execution Price**, and **Size USD** had the highest influence on *Closed PnL*.


###  3. Feature Engineering
- Converted categorical variables (Account, Coin, Side, Direction, Classification) using **Label Encoding**.  
- Removed redundant or non-informative features.  
- Final shape after processing:  
  - **X:** (211,224 × 11)  
  - **y:** (211,224 × 1)



### 4. Model Development & Evaluation
Three regression models were trained and evaluated using RMSE, MAE, and R²:

| Model | RMSE | MAE | R² | Comment |
|--------|------|------|------|----------|
| **Gradient Boosting** |  **0.8743** | 0.0434 |  **0.5620** |  Best overall |
| **Random Forest** | 0.9085 | 0.0135 | 0.5270 | Stable performance |
| **Linear Regression** | 1.3265 | 0.1265 | -0.0082 | Poor — underfits data |

 **Final Model Selected:** *Gradient Boosting Regressor*  
It performed best with low RMSE and high R², effectively capturing complex non-linear patterns.



###  5. Explainable AI (XAI)
Using **SHAP values** and **feature importance**, key insights were derived:
- **Sentiment Score**, **Trade Size (USD)**, and **Execution Price** had the most influence on *Closed PnL*.  
- Positive sentiment contributed to higher profits.  
- Larger trades tended to perform better during *Greed* phases.


###  6. Conclusion
- Market sentiment has a **strong impact** on trader behavior and performance.  
- Traders take **bigger risks and earn more** during *Greed* phases, while becoming **cautious during Fear*.  
- **Gradient Boosting Regressor** achieved the best performance (RMSE = 0.87, R² = 0.56).  
- Combining **sentiment analysis with trading data** helps design smarter, emotion-aware trading strategies in the Web3 ecosystem.










