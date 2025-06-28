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

