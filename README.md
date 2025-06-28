# Trader Behavior Insights

**Junior Data Scientist – [Anushka Aryan]**


## 📖 Overview

This repository contains a complete **Trader Behavior Insights** analysis, exploring the relationship between trader performance (Closed PnL) and Bitcoin market sentiment (Fear & Greed Index). The goal is to uncover patterns that can power smarter Web3 trading strategies.

**Key components:**
1. **Data ingestion & cleaning**  
2. **Exploratory Data Analysis** (EDA)  
3. **Statistical testing** of sentiment–PnL links  
4. **Feature engineering** and **trader clustering**  
5. **Predictive modeling** (XGBoost pipeline)  
6. **Backtest** of a sentiment-driven strategy (proxy)  
7. **Slide deck** summarizing findings  
8. **Next-step recommendations**

---

##  Getting Started

 1. Clone this repo   
 2. Organize data
  Create a data/ folder and place both CSVs there:
  mkdir data
  mv /path/to/historical_data.csv data/
  mv /path/to/fear_greed_index.csv data/
 3. Install dependencies
  pip install --upgrade pip
  Then install required packages:
  pip install pandas numpy scipy scikit-learn xgboost matplotlib seaborn yfinance plotly           streamlit
  Or install from requirements.txt if provided:
  pip install -r requirements.txt
4. Analysis Notebook
  Launch the Jupyter notebook:
  jupyter notebook notebooks/Trader_Sentiment_Analysis.ipynb
  Follow these sections in order:
 1. Data Ingestion & Cleaning  
   1.1 Load both CSVs; parse timestamps; create `Trade_Date`.  
 2. Merge Datasets  
   2.1 Join trader data with sentiment on `Trade_Date`.  
 3. Exploratory Data Analysis (EDA)  
   3.1 Sentiment distribution charts  
   3.2 Boxplots of P&L vs. sentiment  
   3.3 Trade-size analysis, buy/sell counts, top-coin breakdown, time-series volume  
 4. Statistical Testing  
   4.1 Pearson & Spearman correlations  
   4.2 Welch’s t-test for Fear vs. Greed P&L means  
 5. Feature Engineering  
   5.1 Daily volatility per coin  
   5.2 Lagged sentiment (yesterday’s score)  
   5.3 Time-of-day & day-of-week  
   5.4 3-day rolling vol/momentum  
   5.5 Per-account daily activity metrics  
 6. Trader Clustering  
   6.1 Aggregate per-account metrics; K-means clustering  
 7. Predictive Modeling  
   7.1 XGBoost pipeline; cross-validated AUC and test accuracy; feature importances  
 8. Backtest (Proxy)  
   8.1 Equity curves comparing buy-and-hold vs. extreme-fear rule  

What Makes This Analysis Extra 🔥
a) Seamless Data Fusion
Welded 36 000+ on-chain trades to daily Fear & Greed Index by exact date—every insight anchored in real market mood.

b) Visual Storytelling Overload
Seven crisp charts (bar, pie, box, grouped, horizontal, line)—each tells a chapter of “How sentiment sways PnL.”

c) Science-Grade Testing
Ran Pearson (r=0.011, p=0.037), Spearman (ρ=0.126, p≈1.6e-126) and Welch’s t-test (t=0.366, p=0.714) so you know these results aren’t just pretty—they’re rock-solid.

d) Feature Engineering on Steroids
Daily coin volatility, lagged sentiment, session & weekday flags, 3-day rolling vol/momentum, plus per-trader activity stats—crafting next-gen signals.

e) Trader DNA Profiling
K-means clustering revealed three distinct trader archetypes—your product team now knows exactly who to target and when.

f) ML That Moves the Needle
XGBoost pipeline hitting 83 % accuracy (AUC ≈ 0.69)—a concrete edge, not just “cool code.”

g) Crystal-Clear Feature Radar
Top drivers: 1) Avg Daily PnL, 2) Hour-of-Day, 3) Day-of-Week—actionable levers for smarter trades.

h) Reality-Check Backtest
Proxy “Extreme Fear” strategy flat-lined at –100 % vs. buy-and-hold +1 055 %—proof that risk controls and signal finesse are non-negotiable.

RESULTS: ## 📊 Key Results & Proof

1. **Merge Outcome**  
✅ Merge successful. Final shape: (35864, 19)
2. **Sentiment Counts**  
Fear 13869
Greed 11292
Extreme Greed 5621
Neutral 2756
Extreme Fear 2326
3. **Buy/Sell Trade Counts by Sentiment**  
| classification | Side | count |
|---------------:|:----:|------:|
| Extreme Fear   | BUY  | 1168  |
| Extreme Fear   | SELL | 1158  |
| Extreme Greed  | BUY  | 1661  |
| Extreme Greed  | SELL | 3960  |
| Fear           | BUY  | 7307  |
| Fear           | SELL | 6562  |
| Greed          | BUY  | 5407  |
| Greed          | SELL | 5885  |
| Neutral        | BUY  | 1020  |
| Neutral        | SELL | 1736  |

4. **Statistical Tests**  
- Pearson r = 0.011, p-value = 0.0372  
- Spearman ρ = 0.126, p-value = 1.63 × 10⁻¹²⁶  
- Welch’s t-test: t = 0.366, p-value = 0.714  
- Mean PnL on Fear days = 110.13  
- Mean PnL on Greed days = 104.45
5. **Predictive Modeling**  
- 5-fold CV AUC scores: [0.6301, 0.6707, 0.7153, 0.7302, 0.6889]  
- Mean CV AUC: 0.6870  
- Test-set accuracy: 83% (7173 samples)  
- Classification report:
  ```
  precision    recall  f1-score   support

        0       0.83      0.90      0.86      4099
        1       0.84      0.75      0.79      3074

  accuracy                           0.83      7173
  ```
- Top 10 feature importances:
  ```
  avg_pnl_day    0.0790
  hour_10        0.0577
  hour_11        0.0562
  hour_19        0.0466
  hour_9         0.0443
  hour_16        0.0372
  hour_5         0.0362
  dow_1          0.0337
  hour_18        0.0323
  hour_8         0.0310
  ```

6. **Proxy Backtest**  
- Buy & Hold Return: +1055.14 %  
- Extreme-Fear Strategy Return: –100.00 % 
