---
title: "LSTM Forecasting of Bitcoin Implied Volatility (DVOL)"
status: "🟦 Writing Phase"
subtitle: "Master's Thesis – Economics (STEM Designated)"
description: "LSTM neural network model for forecasting Bitcoin implied volatility (DVOL) using on-chain metrics and historical volatility patterns, achieving R² = 0.9287 across a 17-model comparison framework."
keywords: ["LSTM", "Bitcoin", "implied volatility", "DVOL", "deep learning", "forecasting"]
tags: ["deep-learning", "volatility", "bitcoin"]
github_url: "https://github.com/lrud/THESIS"
overview: "This thesis develops and validates a Long Short-Term Memory (LSTM) neural network model for forecasting Bitcoin implied volatility (DVOL), the Deribit 30-day volatility index. Using a unified framework of 17 models (13 linear/tree baselines + 4 LSTM variants), we demonstrate that LSTM models achieve competitive performance (R² = 0.9287) when properly evaluated."
research_objective: "Develop an LSTM neural network model to forecast Bitcoin implied volatility (DVOL) using on-chain metrics and historical volatility patterns, validated through statistical analysis and economic significance."
key_findings:
  - "LSTM with lagged volatility features achieves R² = 0.9287, competitive with best linear/tree models"
  - "41,055 hourly samples with 17-model comparison framework"
  - "Lagged volatility features alone achieve near-optimal performance (7 features)"
  - "All models achieve ~50% directional accuracy - hourly DVOL direction is fundamentally unpredictable"
  - "VaR backtesting passes 95%/99% Kupiec tests - model does not underestimate tail risk"
dataset:
  name: "v1.6_final"
  samples: "41,055 hourly records"
  period: "April 23, 2021 – December 28, 2025"
  jumps: "236 Lee-Mykland jumps (0.57%) using standard Gumbel threshold"
core_predictors:
  - name: "Lagged DVOL"
    description: "1-day, 7-day, 30-day lags"
  - name: "Transaction Volume (USD)"
    description: "Daily on-chain transaction volume"
  - name: "Active Addresses Count"
    description: "Daily count of active Bitcoin addresses"
  - name: "Network Value to Realized Value (NVRV)"
    description: "Market value/realized value ratio"
  - name: "DVOL-RV Spread"
    description: "Volatility risk premium (DVOL - 30-day realized volatility)"
model_architecture:
  type: "LSTM neural network"
  hidden_size: 512
  num_layers: 7
  parameters: "13.8M"
  regularization: "Dropout 0.5, L2 penalty 1e-4"
  normalization: "720-hour rolling window"
results:
  r_squared: 0.9287
  rmse: 1.71
  mae: 1.28
  directional_accuracy: "50.1%"
benchmarks:
  - "HAR-RV (3 features): R² = 0.9454"
  - "Random Forest (11 features): R² = 0.9492"
  - "OLS (11 features): R² = 0.9490"
contributions:
  - "Multi-window normalization analysis: 72-hour window optimal for level prediction"
  - "Standard Lee-Mykland (2008) implementation verification"
  - "Pesaran-Timmermann (1992) directional accuracy methodology"
  - "DataParallel evaluation artifact identification (13.3% R² degradation fix)"
  - "Unified 17-model comparison framework"
technologies: "Python, PyTorch, TensorFlow/Keras, Pandas, NumPy, Scikit-learn, SHAP"
draft: false
---

## Abstract

This thesis develops and validates a Long Short-Term Memory (LSTM) neural network model for forecasting Bitcoin implied volatility (DVOL), the Deribit 30-day volatility index. Using a unified framework of 17 models (13 linear/tree baselines + 4 LSTM variants), we demonstrate that LSTM models achieve competitive performance (R² = 0.9287) when properly evaluated, narrowing the gap to linear/tree models to only 2%.

## Key Contributions

- **Multi-window normalization analysis**: 72-hour (3-day) window is optimal for R² level prediction
- **Standard Lee-Mykland (2008) implementation**: Academically rigorous jump detection with 236 jumps (0.57%)
- **DataParallel evaluation artifact**: Identified 13.3% R² degradation in multi-GPU LSTM evaluation
- **LSTM competitiveness**: With fixed evaluation, LSTM (R²=0.9287) within 2% of best linear/tree models

## Model Comparison Results

All 17 models use identical preprocessing (60/20/20 split, 720h rolling normalization):

| Model | Type | Features | R² | RMSE |
|-------|------|----------|-----|------|
| RF (Lags + Jumps) | Tree | 11 | 0.9492 | 1.65 |
| OLS (Lags + Jumps) | Linear | 11 | 0.9490 | 1.65 |
| HAR-RV | Linear | 3 | 0.9454 | 1.71 |
| **LSTM market_lags** | **LSTM** | **7** | **0.9287** | **1.71** |

## Practical Implications

- **Suitable for**: Risk management, option pricing, volatility level estimation, VaR calculations
- **NOT suitable for**: Directional trading, market timing strategies
- Directional accuracy ~50% across all models indicates hourly direction is fundamentally unpredictable

## Code & Data

The complete codebase, dataset documentation, and reproducibility instructions are available on GitHub.
