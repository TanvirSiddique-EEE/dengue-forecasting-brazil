# Dengue Forecasting in Brazil — A Multi-Model Study

Dengue has been a persistent public health burden across Brazil for decades,
and predicting its spread accurately — even a few weeks ahead — can make a
real difference for health authorities trying to allocate resources in time.

This project started as a course assignment (EEE 4710), but the question it
tries to answer felt genuinely worth exploring: which machine learning
architecture handles the seasonality and spatial variation of dengue cases
best, and by how much?

We tested five different approaches on monthly state-level data from Brazil
and compared them side by side.

---

## What's Inside

The `notebooks/` folder has one file per model, each self-contained and
runnable top to bottom. The dataset lives in `data/`, and the full project
report is in `docs/` if you want the methodology and results in detail.

| Model | Notebook |
|---|---|
| Bidirectional LSTM | `Bi_LSTM.ipynb` |
| GNN Hybrid Structure | `GNN_Hybrid_Structure.ipynb` |
| Multilayer Perceptron | `MLP.ipynb` |
| Temporal Fusion Transformer | `TFT_Temporal_Fusion_Transformer.ipynb` |
| XGBoost + Random Forest | `XGBoost_RandomForest.ipynb` |

---

## The Dataset

`Brazil_UF_dengue_monthly.csv` contains monthly reported dengue cases broken
down by Brazilian state (UF = Unidade Federativa). It covers multiple years,
which gives the models enough history to learn seasonal patterns.

---

## Getting It Running

You'll need Python 3.8+ and the following libraries:

```bash
pip install tensorflow torch scikit-learn xgboost pandas numpy matplotlib seaborn
```

Then just open any notebook in Jupyter and run all cells. Each one loads the
data, preprocesses it, trains the model, and shows evaluation metrics at the
end.

---

## Why These Five Models?

Honestly, because they represent genuinely different philosophies. LSTMs and
TFTs are built for sequences. GNNs capture spatial relationships between
states. MLP is the simple baseline you always need. XGBoost and Random Forest
show how far classical methods can go before deep learning pulls ahead — or
doesn't.

## Results Summary

| Model | R² (Log Scale) | R² (Real Scale) | MAE (cases) | RMSE (cases) | MAPE (%) | Notes |
|---|---|---|---|---|---|---|
| **MLP** | 0.9194 | 0.9194 | 1,257 | — | — | Baseline — strong local feature learning |
| **Hybrid GNN + MLP** | 0.9464 | 0.9464 | 987 | — | — | **Best R²** — captures spatial spread between states |
| **XGBoost** | 0.9317 | 0.9317 | 1,110 | 6,038 | 52.79 | Best real case-count prediction, highest outbreak detection (F1: 0.9257) |
| **Random Forest** | 0.9392 | 0.9392 | 1,171 | 6,996 | 41.83 | Stable ensemble, slightly higher RMSE than XGBoost |
| **Bi-LSTM + Attention** | 0.8241 | 0.5190 | 1,760 | 8,220 | 107.84 | Sequential model — good trend tracking, weaker on outbreak peaks |
| **TFT** | 0.8774 | 0.7151 | 1,195 | 6,326 | 74.92 | **Best sequential model** — 12-month window + static features |

### Key Takeaways
- 🥇 **Best Overall R²:** Hybrid GNN + MLP (0.9464) — spatial awareness between Brazilian states gave it the edge
- 🏆 **Best Real Case Prediction:** XGBoost — lowest MAE (1,110) and RMSE (6,038)
- ⚡ **Best Sequential Model:** TFT outperforms Bi-LSTM on every metric — lower MAE, lower RMSE, lower MAPE, higher R²


## Project Context

**Course:** EEE 4710 — Islamic University of Technology 
 **Year:** 2026

---

## A Note on the Data

The dataset is used here strictly for academic and research purposes.
If you plan to build on this work, double-check the original data source
for any usage restrictions before publishing results.
