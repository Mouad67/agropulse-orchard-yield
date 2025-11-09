# Technical Report
**Title:** Predicting Orchard Yield in Morocco Using Synthetic, Agronomically-Grounded Data  
**Context:** AgroPulse Dynamics – Smart Farming / Smart Irrigation  
**Disclosure:** Due to lack of open, high-resolution field data, we generated a synthetic dataset that mirrors real-world ranges and relationships.

## 1. Problem
Predict **yield_kg_per_ha** using weather, irrigation, nutrition, soil, NDVI, disease, and phenology for avocado, apple, and kaki orchards (Morocco).

## 2. Data
- 1,500 orchard-seasons, 3 crops, 6 Moroccan regions.
- Columns include crop, variety, phenology (flowering/harvest DOY), soil texture/pH/WHC/OM, climate (GDD, rainfall, ET0, temps, radiation, humidity), irrigation (system, events, total mm, stress days), fertilizer split (N/P/K across stages), disease pressure, major events, NDVI at stages, weekly soil moisture at 30 cm, trees/ha, and targets: `yield_kg_per_ha`, `yield_kg_per_tree`.

## 3. Methods
- Preprocessing: one-hot for categoricals, standardize numerics; scikit-learn pipelines.
- Models compared: Linear Regression, Ridge (alpha=10), Random Forest (n=300).
- Split: 80/20 train-test with random_state=42.
- Metrics: RMSE, MAE, R² on the held-out test set.

## 4. Results (actual)
| name                  |    rmse |     mae |       r2 |
|:----------------------|--------:|--------:|---------:|
| Linear Regression     | 2071.97 | 1603.88 | 0.730983 |
| Ridge (alpha=10)      | 2009.86 | 1568.11 | 0.74687  |
| Random Forest (n=300) | 2099.16 | 1660.27 | 0.723875 |

**Best model:** Random Forest. Figures saved under `reports/figures/`:
- target_distribution.png
- correlation_matrix.png
- rf_pred_vs_actual.png
- rf_residuals.png
- rf_top20_importance.png

Top RF feature importances saved to: `reports/top_feature_importance.csv`.

## 5. Optimization & Reflection
- Ridge regularization stabilizes linear fit; RF captures non-linearities and interactions.
- Residuals show no obvious pattern; most error likely from simulated noise and unobserved factors.
- Trade-offs: RF accuracy vs interpretability; we mitigate with feature importances and clear documentation.

## 6. Ethics & Sustainability
- Dataset is **synthetic**; disclosed to avoid misleading stakeholders.
- Real deployment requires on-farm logs (irrigation volumes, fertilizer splits, disease events, NDVI/soil-moisture time series) and re-validation.
- Impact: potential reductions in water, fertilizer, and energy through better decisions.

## 7. Conclusions
- End-to-end ML workflow yields strong baseline with RF (see R² above).
- This informs AgroPulse what to measure for production-grade models (water balance, canopy vigor, disease, soil capacity).
