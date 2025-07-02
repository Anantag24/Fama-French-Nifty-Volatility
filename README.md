📊 Fama-French Factor Modeling \& Volatility Forecasting — Nifty 50 Analysis

This project applies the Fama-French 3-Factor Model to the Indian stock market using Nifty 50 data. It involves constructing SMB and HML factors, regressing stock excess returns, and modeling residual volatility using GARCH and EGARCH models.



🎯 Objective

To evaluate how effectively the Fama-French 3-Factor model explains return variations in Indian large-cap stocks, with a detailed analysis of ICICI Bank, and to explore persistence and asymmetry in volatility using econometric tools.



🔧 Methodology

1\. Data Collection

Period: 5-year daily data (2020–2025)



Source: yfinance



Assets: Nifty 50 constituent stocks



Fundamentals: Shares Outstanding, P/B Ratio



Risk-Free Rate: 91-day T-Bill yield



2\. Factor Construction

SMB (Small Minus Big): Based on median market cap



HML (High Minus Low): Top \& bottom 30% of P/B ratios



MKT\_EXCESS: Nifty 50 daily return – daily risk-free rate



Rebalancing: Annually on June 30



3\. Fama-French Regression

We estimate the following model:



Copy

Edit

Rᵢ - R𝚏 = α + βₘ(Rₘ - R𝚏) + βₛₘ\_b(SMB) + βₕₘₗ(HML) + εᵢ

Estimated via OLS using statsmodels



Residuals extracted for volatility analysis



📈 ICICI Bank — Regression Results

Metric	Value	Interpretation

Alpha (α)	~0.0003	Minimal abnormal return

Beta\_MKT	≈ 1.00	Moves in line with the market

Beta\_SMB	–0.60	Strong large-cap behavior

Beta\_HML	+0.17	Slight value tilt

R²	0.53	53% of return variance explained



📉 GARCH(1,1) Volatility Modeling

Parameter	Value	Interpretation

ω	1.13e‑5	Base level of volatility

α₁	0.10	Moderate reaction to new market shocks

β₁	0.80	Strong volatility persistence (clustering)

μ	Slightly negative	Negative daily return trend over the period



📁 Files in the Repository

ff\_factors.csv — Computed Fama-French factors (SMB, HML, MKT\_EXCESS)



ff3\_regression\_results.csv — Regression coefficients



nifty50\_fundamentals\_with\_pb.csv — Raw P/B and market cap data



Presentation.pdf — Final slides for submission



Summary\_report.pdf — Full project report



python\_code.ipynb — Complete Jupyter analysis notebook



🛠️ Tools \& Libraries

pandas, numpy, yfinance — Data handling



statsmodels — OLS regression



arch — GARCH/EGARCH volatility modeling



matplotlib, seaborn — Plotting and visualization



✅ Key Takeaways

The Fama-French 3-Factor model explains ~53% of ICICI Bank’s excess return variation



GARCH(1,1) captures volatility clustering — a typical market feature



EGARCH has potential to model asymmetric shocks in Indian equities



🧠 Future Scope

Extend model to Fama-French 5-Factor (adding momentum \& profitability)



Apply to mid-cap and small-cap stocks



Integrate results into interactive dashboards (e.g., Streamlit)



Build portfolio optimization tools using factor loadings



👨‍💻 Author

Developed by Ananta Gupta

Undergraduate Research Project | IIT Kanpur

Supervised by: Prof. Wasim Ahmad

