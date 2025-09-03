---
title: 'Projects'
date: 2025-09-02T11:56:21-04:00
draft: true
---

<div style="font-size:1.1em;font-weight:500;line-height:1;margin-bottom:-2.8em;">Master’s Thesis – Economics</div>

## Modeling Bitcoin's Implied Volatility Using Machine Learning
<sub style="display:block;margin-bottom:0.5em;margin-top:-1.2em;font-size:1em;">🟦 In Progress</sub>

**Overview**
This research is being conducted as part of a master's degree in economics. It investigates the unique volatility dynamics of Bitcoin, leveraging state-of-the-art machine learning models such as LSTM and Jordan Neural Networks. The focus is on modeling implied volatility—a key input for options pricing—where academic coverage is limited but practical impact is high.

**Objectives**
- Analyze the drivers of Bitcoin implied volatility
- Compare ML models (LSTM, Jordan NN) with traditional financial models
- Assess the role of internal vs. external market factors

**Technologies Used**
- Python (NumPy, pandas, scikit-learn, TensorFlow, Keras)
- Stata (statistical analysis and data preprocessing)

<span style="font-weight:bold;">Potential Applications</span>
- <span style="text-decoration:underline;">Options Pricing</span>: Enhance the accuracy of Bitcoin options valuation using improved implied volatility models.
- <span style="text-decoration:underline;">Risk Management</span>: Support better hedging and risk assessment for institutional and retail participants in crypto derivatives.
- <span style="text-decoration:underline;">Academic Research</span>: Contribute new methodologies and insights to the literature on digital asset volatility modeling.

---

## Credit Market Volatility Research
<sub style="display:block;margin-bottom:0.5em;margin-top:-1.2em;font-size:1em;">🟩 Completed</sub>

**Overview**
This project investigates how credit market stress impacts the volatility of both Bitcoin and NASDAQ assets. Using a panel data framework and quantile regression, it explores nuanced, heterogeneous effects across different volatility regimes. The analysis highlights the role of credit spreads, Treasury yield curve, and implied volatility in driving asset volatility, with a focus on asset-specific risk transmission.


**Objectives**
- Model the impact of credit market stress on asset volatility
- Compare volatility dynamics between Bitcoin and NASDAQ
- Visualize and interpret quantile regression results

**Technologies Used**
- Stata (panel data prep, regression, quantile regression, table generation)
- Python (pandas, numpy, matplotlib for data visualization)

<a href="https://github.com/lrud/credit-market-volatility-research" style="color:#1976d2;font-weight:600;text-decoration:underline;">
  View the full project and code on GitHub
</a>
{{< carousel >}}

---

## ES Futures VPOC Strategy Backtester
<sub style="display:block;margin-bottom:0.5em;margin-top:-1.2em;font-size:1em;">🟩 Completed</sub>

**Overview**
Advanced algorithmic trading strategy for E-mini S&P 500 (ES) futures that combines Volume Point of Control (VPOC) analysis with statistical validation and machine learning. The strategy identifies high-probability trading opportunities by analyzing volume distribution patterns, value area migrations, and market microstructure. ML enhancements include feature engineering, neural network models, and distributed training for AMD GPUs.


**Objectives**
- Develop and backtest VPOC-based trading strategies
- Integrate machine learning for signal generation and risk management
- Validate strategy performance with statistical and ML metrics

**Technologies Used**
- Python (pandas, numpy, matplotlib, seaborn, scikit-learn, statsmodels, pandas-ta, torch, mpi4py)
- Jupyter Notebooks (strategy prototyping, analysis)

<a href="https://github.com/lrud/futures_vpoc_backtest" style="color:#1976d2;font-weight:600;text-decoration:underline;">
  View the full project and code on GitHub
</a>

<p style="margin-bottom: 1.5em;"></p>
{{< carousel project="futures_vpoc_backtest" >}}
