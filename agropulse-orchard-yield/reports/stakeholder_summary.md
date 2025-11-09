# Stakeholder Summary – Smarter Orchard Yield Insights

**What we built**  
A realistic (synthetic) Moroccan orchard dataset (avocado, apple, kaki) and ML models to predict **yield_kg_per_ha** from weather, irrigation, soil, fertilizer, NDVI, disease, and phenology.

**Results on this dataset**  
| name                  |    rmse |     mae |       r2 |
|:----------------------|--------:|--------:|---------:|
| Linear Regression     | 2071.97 | 1603.88 | 0.730983 |
| Ridge (alpha=10)      | 2009.86 | 1568.11 | 0.74687  |
| Random Forest (n=300) | 2099.16 | 1660.27 | 0.723875 |

**What drives predictions (RF)**  
See `reports/top_feature_importance.csv` and `reports/figures/rf_top20_importance.png` – NDVI stages, irrigation vs ET0, stress days, fertilizer N/K totals, disease pressure, soil WHC/OM, plus crop/region.

**What this is not**  
Real farm logs. It's synthetic for demonstrating a rigorous ML workflow and to design data collection for pilots.

**Next steps**  
1) Instrument pilot blocks (flow meters, soil probes, NDVI).  
2) Log fertilizer splits + disease scouting in the app.  
3) Retrain and validate before any farmer-facing deployment.
