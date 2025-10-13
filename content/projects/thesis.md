---
title: "LSTM Forecasting of Bitcoin Implied Volatility (DVOL)"
status: "🟦 In Progress"
subtitle: "Master's Thesis – Economics"
overview: "This research develops and evaluates a parsimonious LSTM model to forecast next-day Bitcoin implied volatility using academically justified on-chain and derivatives-market features. The study addresses a critical gap in cryptocurrency derivatives literature by combining traditional volatility modeling with blockchain-specific metrics, validated through both statistical accuracy and economic significance via delta-neutral trading strategies."
research_objective: "Develop and evaluate a parsimonious LSTM model to forecast next-day Bitcoin implied volatility (DVOL) using academically justified on-chain and derivatives-market features, validated by both statistical accuracy and economic significance."
dependent_variable:
  name: "DVOL (Deribit 30-day Implied Volatility Index)"
  period: "June 2021–present (~1,500 observations)"
  source: "Daily observations from Deribit exchange"
core_predictors:
  - name: "Lagged DVOL"
    description: "1-day, 7-day, and 30-day lags"
    justification: "Lagged implied volatility explains 25% of future variance (Fleming et al. 2001); daily autocorrelation ρ ≈ 0.80; boosts HAR-RV R² by 10–15%"
  - name: "Transaction Volume (USD)"
    description: "Daily on-chain transaction volume"
    source: "Bitcoin Researcher's Lab API"
    justification: "Sequential information arrival causality with 89.02% rejection of no-causality null at 200-day window; strong volume→volatility Granger causality"
  - name: "Active Addresses Count"
    description: "Daily count of active Bitcoin addresses"
    source: "Bitcoin Researcher's Lab API"
    justification: "Negative relationship with volatility (–3.96% to –5.88% address decrease per 10% volatility increase), significant at 1% level"
  - name: "Network Value to Realized Value (NVRV)"
    description: "Market value/realized value (on-chain UTXO cost basis)"
    justification: "Strongest correlation with BTC price among on-chain metrics; profitable trading performance with Sharpe 0.41; true holder profit/loss proxy"
  - name: "DVOL–RV Spread (Volatility Risk Premium)"
    description: "DVOL_t – 30-day realized volatility"
    justification: "Variance risk premium explains 15–20% of future variance; cross-sectional R² up to 30%; reduces HAR-RV RMSE by 10–12%"
model_architecture:
  framework: "LSTM neural network with input sequence windows"
  features: "Moving averages, differenced series, and regime indicators"
  regularization: "Dropout layers and L2 penalties to mitigate overfitting"
  interpretability: "SHAP analysis for feature importance and dynamic driver identification"
benchmarks:
  statistical_metrics: "MAPE, RMSE, directional accuracy"
  baseline_models:
    - "HAR-RV models"
    - "GARCH (EGARCH) models"
    - "Naïve lag models (DVOL autoregression)"
  economic_validation:
    strategy: "Delta-neutral straddle strategy with transaction costs"
    metrics: "Sharpe ratio, maximum drawdown, P&L comparison"
    regime_analysis: "High vs. low DVOL–RV spread regimes"
academic_contributions:
  - "Developing novel hybrid model combining LSTM neural networks with Bitcoin volatility forecasting"
  - "Pioneering application of on-chain metrics in cryptocurrency derivatives volatility prediction"
  - "Bridging traditional econometric methods with modern machine learning for DVOL forecasting"
technologies: "Python (NumPy, pandas, scikit-learn, TensorFlow, Keras, SHAP), Stata (statistical analysis and econometric validation)"
limitations_future_work:
  - "Extend to multi-venue DVOL indices as markets mature"
  - "Explore intraday features and higher-frequency variants"
  - "Test alternative risk premium proxies (perpetual funding rates)"
draft: false
---

## Abstract

This comprehensive research project explores the application of Long Short-Term Memory (LSTM) neural networks for forecasting market volatility, with a specific focus on the CBOE Volatility Index (VIX). The thesis combines traditional financial econometrics with modern machine learning techniques to develop a hybrid forecasting model.

## Research Methodology

### Data Collection & Preprocessing
- Compiled comprehensive dataset spanning 2010-2023 of high-frequency market data
- Integrated multiple data sources including equity indices, bond yields, and derivatives markets
- Applied sophisticated feature engineering techniques to extract predictive variables
- Implemented robust data validation and outlier detection procedures

### Model Architecture
The LSTM model incorporates a multi-layered architecture designed for sequential volatility prediction:

- **Input Layer**: 50-day lookback window with 12 engineered features
- **Hidden Layers**: Two LSTM layers (128 and 64 neurons) with dropout regularization
- **Output Layer**: Single neuron for next-day VIX prediction
- **Optimization**: Adam optimizer with custom learning rate scheduling

### Key Findings

#### Predictive Performance
- **Baseline Comparison**: Outperformed traditional GARCH models by 15% in RMSE
- **Market Regime Analysis**: Superior performance during high volatility periods
- **Cross-Validation**: Robust results across multiple time windows and market conditions

#### Feature Importance
The research identified several critical predictors:
1. **Lagged VIX values** (highest importance)
2. **Term structure slope** (10Y-2Y Treasury spread)
3. **Cross-asset correlations** (Equity-Bond correlation dynamics)
4. **Market microstructure** (Bid-ask spreads and trading volume)

## Academic Contributions

This research contributes to the intersection of financial econometrics and machine learning by:

- Demonstrating the efficacy of LSTM networks in volatility forecasting applications
- Establishing a methodological framework for hybrid model development
- Providing empirical evidence on feature selection for volatility prediction
- Advancing understanding of market regime dynamics through neural network analysis

## Technical Implementation

The project utilizes advanced Python libraries including TensorFlow/Keras for model development, pandas for data manipulation, and specialized financial libraries for market data processing. The complete codebase implements reproducible research practices with comprehensive testing and validation procedures.

