\# Fama-French Factor Modeling \& Volatility Forecasting — Nifty 50 Analysis



This project applies the \*\*Fama-French 3-Factor Model\*\* to the Indian stock market using \*\*Nifty 50\*\* data. It involves constructing SMB and HML factors, regressing stock excess returns, and modeling volatility in the unexplained component (residuals) using \*\*GARCH and EGARCH\*\* models.



---



\## 📌 Objective



To evaluate how effectively the Fama-French 3-Factor model explains return variations in Indian large-cap stocks, specifically focusing on \*\*ICICI Bank\*\*, and to analyze the persistence and asymmetry in volatility using \*\*econometric tools\*\*.



---



\## 🔧 Methodology



\### 1. Data Collection

\- 5-year daily data (2020–2025) fetched via `yfinance`

\- Assets: Nifty 50 stocks

\- Additional fundamentals: \*\*Shares Outstanding\*\*, \*\*P/B ratio\*\*

\- Risk-Free Rate: \*\*91-day T-bill yield\*\*



\### 2. Factor Construction

\- \*\*SMB (Small Minus Big):\*\* Based on median market cap

\- \*\*HML (High Minus Low):\*\* Top \& bottom 30% of P/B ratio

\- \*\*MKT\_EXCESS:\*\* Nifty 50 daily return – risk-free rate

\- \*\*Rebalancing:\*\* Annually on June 30



\### 3. Fama-French Regression

We estimate:

Rᵢ - R𝚏 = α + βₘ(Rₘ - R𝚏) + βₛₘ\_b(SMB) + βₕₘₗ(HML) + εᵢ



\- Estimated via OLS (`statsmodels`)

\- Residuals captured for volatility modeling



---



\## 📈 ICICI Bank: Regression \& Volatility Results



\### Fama-French Regression:



| Metric      | Value     | Interpretation                      |

|-------------|-----------|--------------------------------------|

| \*\*βₘ\*\*      | ≈ 1.00    | Moves in line with the market       |

| \*\*βₛₘ\_b\*\*   | –0.60     | Strong large-cap behavior           |

| \*\*βₕₘₗ\*\*    | +0.17     | Slight value tilt                   |

| \*\*Adj R²\*\*  | 0.53      | 53% of return variance explained    |

| \*\*α\*\*       | ~0.0003   | Minimal abnormal return             |



---



\### GARCH(1,1) Volatility Modeling:



| Parameter  | Value     | Interpretation                                   |

|------------|-----------|--------------------------------------------------|

| \*\*ω\*\*      | 1.13e-5   | Base volatility level                            |

| \*\*α₁\*\*     | 0.10      | Moderate reaction to new market shocks           |

| \*\*β₁\*\*     | 0.80      | Strong volatility persistence (clustering)       |

| \*\*μ\*\*      | Slightly negative | Negative daily return trend over period  |



---



\## 📁 Files in the Repository



\- `ff\_factors.csv` – Computed Fama-French factors (SMB, HML, MKT\_EXCESS)

\- `ff3\_regression\_results.csv` – Coefficients for all stocks

\- `nifty50\_fundamentals\_with\_pb.csv` – Raw fundamentals (P/B, Market Cap)

\- `Presentation.pdf` – Final presentation slides

\- `Summary\_report.pdf` – Detailed project report

\- `python\_code.ipynb` – All code (factor creation, regressions, volatility modeling)



---



\## 🛠️ Tools \& Libraries



\- `pandas`, `numpy`, `yfinance` – Data handling

\- `statsmodels` – OLS regressions

\- `arch` – GARCH \& EGARCH modeling

\- `matplotlib`, `seaborn` – Visualizations



---



\## ✅ Key Takeaways



\- The Fama-French 3-Factor model \*\*explains ~53%\*\* of ICICI Bank’s return variation.

\- \*\*GARCH(1,1)\*\* confirms \*\*volatility clustering\*\*, a hallmark of financial time series.

\- \*\*EGARCH\*\* offers potential for modeling \*\*asymmetric volatility shocks\*\* — valuable in Indian equity markets.



---



\## 🧠 Future Scope



\- Extend to \*\*Fama-French 5-Factor Model\*\*

\- Apply to \*\*mid-cap/small-cap\*\* Indian indices

\- Integrate with \*\*Streamlit dashboard\*\* for interactive results

\- Use \*\*rolling regressions\*\* for time-varying beta analysis



---



\## 👨‍💻 Author



\*\*Ananta Gupta\*\*  

Undergraduate Research Project | IIT Kanpur  

Supervised by: \*\*Prof. Wasim Ahmad\*\*



