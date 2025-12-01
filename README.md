
# 📈 NIFTY 50 Return & Volatility Analysis

### *Factor Modeling Using Fama–French + Rolling Regression + GARCH / EGARCH*

---

### **📌 Overview**

This research analyzes the return behavior of the **NIFTY 50 index (2020–2025)** using the **Fama-French Three-Factor Model**, volatility diagnostics, and rolling-window sensitivity estimation. The study constructs **custom SMB and HML factors** for the Indian market and applies volatility forecasting techniques (**GARCH & EGARCH**) to detect persistence, asymmetry, and market regime dynamics.

---

### 🎯 **Research Objective**

To evaluate whether the **Fama-French Three-Factor Model** explains excess return variation across the NIFTY 50 constituents and to examine the behavior of residual volatility using time-series econometric models.

---

## 🛠️ Methodology

### **1️⃣ Data Collection**

* Universe: **All NIFTY 50 stocks**
* Frequency: **Daily observations (2020–2025)**
* Source: `yfinance`
* Fundamentals: **Market Cap, Price-to-Book, Shares Outstanding**
* Risk-free rate: **91-day Treasury Bill Yield**

---

### **2️⃣ Factor Construction**

| Factor                         | Construction Basis                        |
| ------------------------------ | ----------------------------------------- |
| **MKT (Market Excess Return)** | NIFTY TRI – Risk-free rate                |
| **SMB (Small − Big)**          | Median market-cap split portfolio returns |
| **HML (High − Low)**           | Top vs. bottom 30% portfolios by P/B      |

📌 **Rebalanced annually (June 30)**

---

### **3️⃣ Fama-French Regression Model**

[
R_i - R_f = \alpha + \beta_m(R_m - R_f) + \beta_{SMB}(SMB) + \beta_{HML}(HML)
]

* Estimated via **OLS (`statsmodels`)**
* Residuals stored for volatility modeling

---

## 📊 Cross-Section Results Summary (NIFTY 50)

| Metric      | α        | β_MKT  | β_SMB   | β_HML   | R²     | Adj. R² |
| ----------- | -------- | ------ | ------- | ------- | ------ | ------- |
| **Mean**    | 0.00019  | 0.9797 | 0.3186  | 0.0530  | 0.3442 | 0.3426  |
| **Median**  | 0.00021  | 0.9995 | 0.4091  | -0.0138 | 0.3368 | 0.3352  |
| **Minimum** | -0.00043 | 0.5380 | -1.3125 | -0.7107 | 0.1564 | 0.1544  |
| **Maximum** | 0.00135  | 1.4307 | 1.7598  | 1.0861  | 0.5762 | 0.5752  |

📌 Interpretation:

* Market exposure averages near **1**, confirming strong systematic influence.
* **SMB factor is positive on average**, indicating presence of a mild small-cap effect even within large-cap universe.
* HML values cluster around **0**, suggesting weak value/growth premium within NIFTY 50.
* Model explains ~**34% of daily excess return variance**, leaving meaningful idiosyncratic risk.

---

## 🔥 Case Example: ICICI BANK

| Parameter   | Value                           |
| ----------- | ------------------------------- |
| β_MKT       | **1.00**                        |
| β_SMB       | **−0.60** (Large-cap tilt)      |
| β_HML       | **+0.17** (Weak value tendency) |
| Adjusted R² | **0.53**                        |
| Alpha       | **≈0** → no abnormal return     |

---

## 📉 Volatility Modeling Results

### **GARCH(1,1)**

| Parameter         | Estimate                              |
| ----------------- | ------------------------------------- |
| ω                 | 1.13e-5                               |
| α₁                | 0.10                                  |
| β₁                | 0.80                                  |
| Persistence (α+β) | **0.90 → High volatility clustering** |

### **EGARCH(1,1)**

* Reveals **negative asymmetry (leverage effect)**
  ➡️ Volatility reacts more strongly to negative news than positive shocks.

---

## 📁 Repository Contents

| File                         | Description                                |
| ---------------------------- | ------------------------------------------ |
| `ff_factors.csv`             | Constructed SMB, HML, and MKT factors      |
| `ff3_regression_results.csv` | Regression outputs for all NIFTY 50 stocks |
| `python_code.ipynb`          | Complete workflow                          |
| `Summary_Report.pdf`         | Full academic documentation                |
| `Presentation.pdf`           | Slide deck version                         |

---

## 🧪 Tools & Libraries

* `pandas`, `numpy`, `yfinance`
* `statsmodels` (econometric estimation)
* `arch` (GARCH & EGARCH models)
* `matplotlib`, `seaborn` (visualization)

---

## 🎯 Key Takeaways

* The **market factor dominates** return variation in NIFTY 50.
* Evidence of a **mild size premium (SMB)**; growth/value effect (HML) is weak.
* Volatility is **persistent, clustered, and asymmetric**, validating GARCH-type models.
* The factor structure provides a strong foundation for **factor-based investing** in India.

---

## 🚀 Future Enhancements

* Expand to **Fama-French Five-Factor and Six-Factor Models**
* Apply **Kalman-Filter–based time-varying betas**
* Deploy **Streamlit analytics dashboard**
* Explore **factor-tilted portfolio construction & backtesting**

---

## 👨‍💻 Author

**Ananta Gupta**
📍 IIT Kanpur — Undergraduate Research Project
Mentor: **Prof. Wasim Ahmad**

