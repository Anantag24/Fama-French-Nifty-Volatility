
---

# 📊 Fama-French Factor Modeling & Volatility Forecasting — NIFTY 50 Study

This project implements the **Fama-French Three-Factor Model** on the Indian equity market using the **NIFTY 50 universe (2020–2025)**. Custom SMB and HML factors were constructed based on market capitalization and value characteristics. Factor exposures were estimated for all NIFTY 50 constituents, and volatility in model residuals was analyzed using **GARCH and EGARCH models** to capture persistence and asymmetry in return dynamics.

---

## 🎯 Objective

To evaluate how effectively the **Fama-French 3-Factor Model explains excess return variation across the NIFTY 50 index**, and to model volatility behavior in residuals using econometric volatility forecasting techniques.

---

## 🛠️ Methodology

### **1. Data Collection**

* Universe: **All NIFTY 50 stocks**
* Frequency: **Daily data (2020–2025)**
* Source: `yfinance`
* Fundamental variables: **Market Cap, Shares Outstanding, Price-to-Book Ratio**
* Risk-free proxy: **91-day Treasury bill yield**

---

### **2. Factor Construction**

| Factor                    | Method                                              |
| ------------------------- | --------------------------------------------------- |
| **SMB (Small Minus Big)** | Formed by median split on market cap                |
| **HML (High Minus Low)**  | Formed using top vs. bottom 30% based on P/B ratios |
| **Market Excess Return**  | NIFTY Total Return Index minus daily risk-free rate |
| **Rebalancing Frequency** | Annually on June 30                                 |

---

### **3. Regression Model**

[
R_i - R_f = \alpha + \beta_m(R_m - R_f) + \beta_{SMB}(SMB) + \beta_{HML}(HML) + \epsilon_i
]

* Model estimated using **OLS (statsmodels)**
* **Residuals extracted for volatility forecasting**

---

## 📈 Sample Factor Loadings (Example: ICICI Bank)

| Metric      | Value    | Interpretation                              |
| ----------- | -------- | ------------------------------------------- |
| βₘ          | ≈ 1.00   | Moves closely with market                   |
| βₛₘᵦ        | –0.60    | Large-cap premium (negative SMB exposure)   |
| βₕₘₗ        | +0.17    | Mild value tilt                             |
| Adjusted R² | **0.53** | Model explains majority of return variation |
| Alpha (α)   | ~0.0003  | No significant abnormal return              |

---

## 📉 Volatility Modeling (Residuals)

Using **GARCH(1,1)**:

* ω = 1.13e-5
* α₁ = 0.10
* β₁ = 0.80
* Persistence: **α₁ + β₁ = 0.90 → High volatility persistence**

EGARCH modeling revealed **negative asymmetry (leverage effect)**, indicating volatility increases more following negative shocks — consistent with financial market behavior.

---

## 📚 Files Included

| File                         | Contents                                     |
| ---------------------------- | -------------------------------------------- |
| `ff_factors.csv`             | Market, SMB, and HML factors                 |
| `ff3_regression_results.csv` | Factor sensitivities for all NIFTY 50 stocks |
| `nifty_fundamentals.csv`     | Market cap, P/B, size buckets                |
| `python_code.ipynb`          | Complete implementation pipeline             |
| `Presentation.pdf`           | Final presentation slides                    |
| `Summary_report.pdf`         | Research documentation                       |

---

## 🧠 Tools & Libraries

* `pandas`, `numpy`, `yfinance` — Data collection & wrangling
* `statsmodels` — Fama-French regression
* `arch` — GARCH & EGARCH volatility modeling
* `matplotlib`, `seaborn` — Visualization

---

## ✅ Key Insights

* The **Fama-French model explains a significant share of return variation across NIFTY 50 constituents**
* **Large-cap bias dominates**, reflected in negative SMB loadings for many benchmark components
* **HML factor remains weak/moderate**, aligning with historically growth-oriented Indian blue-chip stocks
* Residual volatility is **persistent and asymmetric**, validating GARCH-type structures for Indian markets

---

## 🚀 Future Scope

* Extend to **Fama-French Five-Factor and Six-Factor Models**
* Expand sample to **NIFTY 500, Midcap, and Smallcap indices**
* Add **rolling window beta visualization and regime detection**
* Build a **Streamlit dashboard for interactive factor analytics**
* Perform **portfolio optimization based on factor exposures**

---

## 👨‍💻 Author

**Ananta Gupta**
Undergraduate Research Project — IIT Kanpur
Supervised by **Prof. Wasim Ahmad**

---


