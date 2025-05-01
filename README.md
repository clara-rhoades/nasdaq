# 📈 NASDAQ Index Close Price Predictions with LSTMs  
**INFO 207 Final Project – Spring 2025**  
Isaac Dallas, Yanling Liu, Clara Rhoades, Coco Sun

---

## 📌 Overview  
This project investigates whether incorporating macroeconomic indicators improves the performance of LSTM models in predicting the NASDAQ index. While most financial models focus on price history and technical indicators, we experimented with adding features like interest rates, inflation, and money supply to assess their impact on model accuracy.

---

## 🎯 Project Goals  
- Predict the next-day NASDAQ closing price using deep learning  
- Compare LSTM model performance with vs. without macroeconomic data  
- Engineer and evaluate long-term financial features (e.g. 90-day highs/lows)  
- Fine-tune hyperparameters to optimize accuracy  
- Explore generalizability and ethical considerations of financial forecasting models  

---

## 🧠 Data Sources  
| Source | Type | Variables |
|--------|------|-----------|
| `yfinance` | Market data | Open, Close, High, Low, Volume, TLT prices, VIX |
| FRED | Macroeconomic | FEDFUNDS, DGS10, CPIAUCSL, PPIACO, M2SL |
| Engineered | Derived | MACD, MACD Signal, MACD Histogram, Yield Spread |

- **Date Range**: 2020-01-01 to 2024-12-31  
- **Lag Handling**: Macro variables shifted to account for reporting delays (e.g., CPI = 45-day lag)  
- **Missing Values**: Forward-filled after lag adjustment  

---

## 🧪 Experiments  
| Model | Features Used | Val MAE | Test MAE |
|-------|----------------|---------|----------|
| Naïve Avg. Predictor | Avg Close Price | $978.37 | $5,298.17 |
| LSTM (All Features) | Stock + Macro + Engineered | $2,643.66 | $5,174.76 |
| **Tuned LSTM (All)** | Stock + Macro + Engineered | $477.50 | $3,251.96 |
| LSTM (Price Only) | 90-Day High/Low | $113.11 | **$159.78** |

---

## 🧮 Feature Engineering  
| Feature | Description |
|--------|-------------|
| MACD, Signal, Hist | Captures momentum & price trend reversals |
| Yield Spread | Measures slope of yield curve (DGS10 - FEDFUNDS) |
| 90-Day High/Low | Long-term trend indicators that improved accuracy |

---

## 🗂 Files & Notebooks  
| File | Description |
|------|-------------|
| `nasdaq_EDA.ipynb` | Loads and cleans yfinance data. Exploratory data analysis |
| `nasdaq_all_features.ipynb` | Merges yfinance with FRED + engineered features. Runs models with all features. |
| `nasdaq_yfinance_features.ipynb` | Runs models with yfinance features. |
| `nasdaq_slides.pdf` | Final project slides for presentation |

---

## 🚀 Key Findings  
- Macroeconomic features **reduced** model performance due to noise and lag  
- Long-term price trends (90-day highs/lows) were highly predictive  
- Optimal model: 1 LSTM layer, 64 units, 0.01 LR, dropout = 0.1  
- Larger models or more neurons ≠ better performance  

---

## ⚖️ Limitations & Ethics  
- **Scope**: Results only apply to NASDAQ index  
- **Risk**: Models like this could be misused in retail trading  
- **Assumptions**: LSTMs assume temporal stability and ignore exogenous shocks (e.g., COVID)  

---

## 🛠 Tools & Tech  
- Python, Pandas, NumPy, Matplotlib  
- TensorFlow/Keras  
- `yfinance`, `pandas_datareader`  
- Local machine training only  

---

## 📚 References  
- Du et al. (2023): Macro factors & SSE index  
- Barth et al. (2019): Macro data predicts US index trends  
- [yfinance](https://github.com/ranaroussi/yfinance) | [FRED](https://fred.stlouisfed.org/) | [Slidesgo](https://slidesgo.com/)  

---
