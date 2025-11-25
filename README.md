# 📊 Trader Behavior Insights — Data Science Assignment  
### Candidate: Aryan Manchanda  
Repository: `ds_AryanManchanda`

---

## 📁 Project Overview

This project analyzes how **market sentiment (Fear/Greed Index)** aligns or diverges from **trader performance** using Hyperliquid’s historical trading data.  
The objective is to uncover behavioral patterns, risk tendencies, and performance shifts relative to market sentiment and identify whether sentiment contains predictive value for PnL.

This assignment was completed as part of the evaluation for the role:  
**Junior Data Scientist – Trader Behavior Insights**

---

## 🚀 Key Objectives

- Load, clean, and structure both datasets (Sentiment + Hyperliquid trader data).
- Engineer meaningful daily trader metrics.
- Merge trader activity with sentiment classification.
- Perform Exploratory Data Analysis (EDA) with multiple visualizations.
- Conduct statistical tests to measure differences between Fear & Greed regimes.
- Analyze predictive relationships (lag correlations, event studies).
- Summarize insights & actionable conclusions in a final report.

---

## 📂 Repository Structure

This repository follows the submission structure required by the hiring team:

```
ds_AryanManchanda/
│
├── notebook_1.ipynb                # Main Colab notebook (all analysis)
├── notebook_2.ipynb                # Optional additional notebook
│
├── csv_files/                      # Cleaned & processed datasets
│   ├── traders_clean.csv
│   ├── sentiment_clean.csv
│   ├── daily_trader_agg.csv
│   └── merged_sentiment_trader.csv
│
├── outputs/                        # All saved visualizations
│   ├── pnl_vs_sentiment.png
│   ├── leverage_by_sentiment.png
│   ├── leverage_vs_pnl_scatter.png
│   ├── volume_vs_sentiment.png
│   ├── feature_corr_heatmap.png
│   ├── lag_corr_sentiment_pnl.png
│   ├── top_traders_pnl.png
│   └── event_study_sentiment_shock.png
│
├── ds_report.pdf                   # Final report with insights
└── README.md                       # This file
```


## 📥 Dataset Sources

1. **Hyperliquid Historical Trader Data**  
   https://drive.google.com/file/d/1IAfLZwu6rJzyWKgBToqwSmmVYU6VbjVs/view?usp=sharing

2. **Bitcoin Fear & Greed Index**  
   https://drive.google.com/file/d/1PgQC0tO8XN-wqkNyghWc_-mnrYv_nhSf/view?usp=sharing

---

## 🛠️ Methodology Summary

### **1. Data Cleaning**
- Standardized and normalized column names  
- Parsed timestamps (`timestamp_ist` localized to Asia/Kolkata → UTC)  
- Created `date` column (UTC midnight)  
- Constructed unified `size` field (`size_usd` → fallback to `size_tokens`)  
- Converted numeric fields (`execution_price`, `closed_pnl`, `fee`, etc.)  
- Normalized `side` values (long/short)  
- Handled missing values and invalid rows  

---

### **2. Feature Engineering**

Daily aggregates computed:

| Feature | Description |
|---------|-------------|
| `daily_volume` | Sum of absolute trade sizes |
| `daily_trades` | Number of trades executed |
| `daily_net_pnl` | Total closed PnL of the day |
| `daily_winrate` | Fraction of profitable trades |
| `daily_avg_position` | Avg. position size per trade |
| `daily_avg_leverage` | Daily leverage mean (NaN if unavailable) |

---

### **3. Sentiment Integration**

- Sentiment classifications normalized to `Fear` / `Greed`.
- Created binary `sentiment_value`: **Fear = 0**, **Greed = 1**.
- Merged with trader aggregates on daily timestamps.

---

## 📊 Exploratory Data Analysis (EDA)

Key visualizations saved in `/outputs/`:

- **Daily PnL vs Sentiment**
- **Volume Trends**
- **PnL Distribution Across Sentiment Regimes**
- **Lag Correlation: sentiment(t) → pnl(t+lag)**
- **Top Trader Cumulative PnL**
- **Event Study: Sentiment Flips**

---

## 🧪 Statistical Tests

| Test | Purpose | Result Summary |
|------|---------|----------------|
| Mann–Whitney U | Compare PnL: Fear vs Greed | No significant difference |
| Chi-square | Profitable day proportion | No significant difference |
| Lag Correlation | Predictive power | No meaningful lag effect |
| Permutation Test | Validate significance | All lags non-significant |

---

## 🎯 Key Insights

- Market sentiment (Fear/Greed) **does NOT significantly explain or predict** daily trader PnL.
- No meaningful lag effects found from 0–7 days.
- Trader performance appears **independent of broad sentiment regimes**.
- Volume and PnL patterns are more influenced by **trader behavior**, not sentiment.
- No leverage information was provided in the dataset, so leverage-related behavior could not be analyzed.

---

## 📄 Final Report

The complete analysis, visualizations, and insights are detailed in:  
**`ds_report.pdf`**

---