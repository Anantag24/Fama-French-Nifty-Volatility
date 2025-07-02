### **📊 Fama-French Factor Modeling \& Volatility Forecasting — Nifty 50 Analysis**

#### 

This project applies the Fama-French 3-Factor Model to the Indian stock market using NIFTY 50 data. It constructs SMB and HML factors, performs excess return regression, and models volatility using GARCH and EGARCH techniques — with a focus on ICICI Bank.



---



#### 🎯 Objective



To evaluate how effectively the Fama-French 3-Factor Model explains return variations in ICICI Bank, and to model volatility patterns in the residuals using econometric methods.



---



#### 🛠️ Methodology



1. ###### Data Collection



* Daily data from 2020–2025 using `yfinance`
* Nifty 50 stocks
* Added fundamentals: Shares Outstanding, P/B ratio
* Risk-free rate: 91-day T-bill yield



###### 2\. Factor Construction



* SMB(Small Minus Big): Size split using median market cap
* HML(High Minus Low): Value sorted using top \& bottom 30% P/B ratios
* MKT\\\_EXCESS: NIFTY return minus daily risk-free rate
* Rebalanced annually on June 30

###### 

###### 3\. Fama-French Regression 



&nbsp;Rᵢ - Rf = α + βₘ(Rₘ - Rf) + β\_SMB(SMB) + β\_HML(HML) + εᵢ



* &nbsp;Estimated using OLS (statsmodels)
* &nbsp;Residuals stored for volatility modeling



---

##### 

##### 📈 ICICI Bank: Model Output



###### Fama-French Regression Results



| Metric   | Value     | Interpretation                        |



| βₘ       | ≈ 1.00    | Moves in line with the market         |

| β\\\_SMB   | –0.60     | Strong large-cap tilt                  |

| β\\\_HML   | +0.17     | Mild value orientation                 |

| Adj R²   | 0.53      | Model explains 53% of return variation |

| α (Alpha)| \\~0.0003  | Negligible abnormal return             |



---



###### GARCH(1,1) Volatility Results





* ω  = 1.13e-5                           
* α₁  =  0.10           
* β₁  =  0.80    
* α₁ + β₁ = 0.90 (volatility is highly persistent)     

---



###### 📁 Files in Repository



* ff\_factors.csv — Constructed SMB, HML, MKT\\\_EXCESS
* ff3\_regression\_results.csv — Stock-wise regression coefficients
* nifty50\_fundamentals\_with\_pb.csv — Raw fundamentals
* Presentation.pdf — Final slides
* Summary\_report.pdf — Full project documentation
* python\_code.ipynb — End-to-end implementation



---



###### &nbsp;📚 Tools Used



* pandas`, `numpy`, `yfinance` — Data processing
* statsmodels` — Regression analysis
* arch` — GARCH, EGARCH volatility modeling
* matplotlib`, `seaborn` — Visualizations



---



###### ✅ Key Insights



* Fama-French model explains \\~53% of ICICI Bank’s excess returns
* Volatility is persistent — captured well by GARCH
* EGARCH reveals asymmetry — important for Indian market dynamics



---



###### 🚀 Future Scope



* Expand to Fama-French 5-Factor Model
* Include mid-cap and small-cap indices
* Build interactive dashboards (e.g., Streamlit)
* Integrate factor-based portfolio optimization



---



###### 👨‍💻 Author



Developed by Ananta Gupta

Undergraduate Research Project | IIT Kanpur

Supervised by: Prof. Wasim Ahmad





