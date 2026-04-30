# Dengue Forecasting in Brazil — Multi-Model Comparison

## Overview
Comparison of machine learning models for forecasting dengue cases
across Brazilian states using monthly epidemiological data.

## Models Implemented
| Model | File |
|-------|------|
| Bidirectional LSTM | `notebooks/Bi_LSTM.ipynb` |
| GNN Hybrid | `notebooks/GNN_Hybrid_Structure.ipynb` |
| MLP | `notebooks/MLP.ipynb` |
| Temporal Fusion Transformer | `notebooks/TFT_Temporal_Fusion_Transformer.ipynb` |
| XGBoost + Random Forest | `notebooks/XGBoost_RandomForest.ipynb` |

## Dataset
- **Source:** Brazil state-level dengue monthly cases
- **File:** `data/Brazil_UF_dengue_monthly.csv`

## Requirements
```bash
pip install tensorflow scikit-learn xgboost pandas numpy matplotlib
```

## Course
EEE 4710 — Islamic University of Technology
