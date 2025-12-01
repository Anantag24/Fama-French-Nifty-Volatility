# 📈 NIFTY 50 Return & Volatility Analysis

### *Factor Modeling Using Fama–French, Rolling Betas, GARCH & EGARCH*

---

## 📌 Overview

This research analyzes the return dynamics of the **NIFTY 50 constituents (2020–2025)** using the **Fama–French Three-Factor Model** along with volatility modeling techniques. The study develops **India-specific SMB and HML factors**, estimates factor exposure for each security, and evaluates **time-varying sensitivity, volatility persistence, and leverage effects** using:

* **OLS regressions**
* **Rolling-window beta estimation**
* **GARCH(1,1)**
* **EGARCH(1,1)**

---

## 🎯 Research Objective

To examine whether the Fama–French model explains cross-sectional variation in excess returns across the NIFTY 50 and to assess volatility behavior in residual returns using econometric forecasting models.

---

## 🛠️ Methodology

### **1️⃣ Data Collection**

| Component      | Specification                             |
| -------------- | ----------------------------------------- |
| Dataset        | NIFTY 50 Constituents                     |
| Frequency      | Daily Prices (2020–2025)                  |
| Source         | `yfinance`                                |
| Fundamentals   | Market Cap, Shares Outstanding, P/B Ratio |
| Risk-Free Rate | 91-Day Treasury Bill Yield                |

---

### **2️⃣ Factor Construction**

| Factor  | Method                                      | Notes                      |
| ------- | ------------------------------------------- | -------------------------- |
| **MKT** | NIFTY TRI − risk-free rate                  | Market excess return       |
| **SMB** | Small-cap minus large-cap portfolio returns | Based on median market cap |
| **HML** | High book-to-market minus low               | Based on P/B deciles       |

📌 **Factors rebalance annually (June 30)**.

---

### **3️⃣ Fama-French Regression Model**

The excess return of each stock is modeled as:

$$
R_i - R_f = \alpha

* \beta_m (R_m - R_f)
* \beta_{SMB} \cdot SMB
* \beta_{HML} \cdot HML
  $$

Where:

* ( \alpha ) → abnormal return
* ( \beta_m ) → sensitivity to market excess return
* ( \beta_{SMB} ) → size premium exposure
* ( \beta_{HML} ) → value–growth exposure

✔ Estimated using **OLS (`statsmodels`)**
✔ **Residuals used for volatility forecasting**

---

## 📊 Fama–French Regression Summary (Across NIFTY 50)

| Statistic  | α        | β_MKT  | β_SMB   | β_HML   | R²     | Adj. R² |
| ---------- | -------- | ------ | ------- | ------- | ------ | ------- |
| **Mean**   | 0.00019  | 0.9797 | 0.3186  | 0.0530  | 0.3442 | 0.3426  |
| **Median** | 0.00021  | 0.9995 | 0.4091  | −0.0138 | 0.3368 | 0.3352  |
| **Min**    | −0.00043 | 0.5380 | −1.3125 | −0.7107 | 0.1564 | 0.1544  |
| **Max**    | 0.00135  | 1.4307 | 1.7598  | 1.0861  | 0.5762 | 0.5752  |

📌 **Interpretation**

* The average **β ≈ 1**, confirming strong systematic market influence.
* **SMB is positive**, indicating a mild size effect.
* **HML is near zero**, suggesting weak value–growth differentiation.
* On average, the model explains **~34% of return variance**, implying meaningful idiosyncratic risk remains.

---

## 🧪 Example Output (ICICI Bank)

| Parameter | Value     | Interpretation            |
| --------- | --------- | ------------------------- |
| β_MKT     | **1.00**  | Moves in line with market |
| β_SMB     | **−0.60** | Large-cap tilt            |
| β_HML     | **+0.17** | Weak value exposure       |
| Adj. R²   | **0.53**  | Good explanatory power    |
| Alpha     | ≈0        | No abnormal return        |

---

## 📉 Volatility Modeling

### 🔹 GARCH(1,1)

| Parameter   | Estimate | Insight                        |
| ----------- | -------- | ------------------------------ |
| ω           | 1.13e-5  | Baseline variance              |
| α₁          | 0.10     | Reaction to new shocks         |
| β₁          | 0.80     | Persistence of volatility      |
| **α₁ + β₁** | **0.90** | **High volatility clustering** |

---

### 🔹 EGARCH(1,1)

* Captures **leverage effect (asymmetry)**
* Negative shocks → **larger volatility spikes** than positive shocks

📌 Indicates **behavior consistent with emerging market microstructure**.

---

## 📁 Project Files

| File                         | Description         |
| ---------------------------- | ------------------- |
| `ff_factors.csv`             | Constructed factors |
| `ff3_regression_results.csv` | Regression outputs  |
| `python_code.ipynb`          | Full implementation |
| `Summary_Report.pdf`         | Written analysis    |
| `Presentation.pdf`           | Slide version       |

---

## 🧰 Tools & Libraries

`pandas` · `numpy` · `yfinance`
`statsmodels` · `arch`
`matplotlib` · `seaborn`

---

## 🎯 Key Insights

✔ Market factor dominates return behavior
✔ Mild size premium present
✔ Weak value/growth differentiation
✔ Volatility is persistent, asymmetric, and clustered
✔ Supports factor-based Indian equity modeling

---

## 🚀 Future Work

* Extend to **Fama-French Five-Factor / Six-Factor Models**
* Perform **machine learning–based return forecasting**
* Build **Streamlit-based interactive dashboard**
* Construct and backtest **factor-tilted portfolios**

---

## 👨‍💻 Author

**Ananta Gupta**
📍 IIT Kanpur — Undergraduate Research Project
Supervisor: **Prof. Wasim Ahmad**
