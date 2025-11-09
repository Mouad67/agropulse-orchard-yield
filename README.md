# AgroPulse Dynamics – Moroccan Orchard Yield (Synthetic)

**Status:** Synthetic dataset engineered for machine-learning training.  
**Crops:** Avocado, Apple, Kaki (Persimmon).  
**Geography:** Morocco (semi-arid Mediterranean; regions: Souss-Massa, Gharb, Tadla, Haouz, Loukkos, Moulouya).

## Why synthetic?
Open, granular field-season data with full irrigation, fertilizer, NDVI time series, and yield is scarce. To complete the capstone and keep it realistic, we generated a **synthetic but agronomically grounded** dataset that preserves plausible relationships (water, canopy vigor, nutrients, disease, etc.) so that regression models can learn (expected R² ~ 0.6–0.8 with tree ensembles).

## File
- `data/moroccan_orchard_yield_synthetic.csv` – 1,500 rows (one orchard-season per row).

## Columns (selected)
- crop, variety, planting_year, flowering_doy, harvest_start_doy, harvest_end_doy
- region, soil_texture, soil_ph, soil_water_holding_capacity_pct, soil_organic_matter_pct, soil_depth_cm
- seasonal_gdd, seasonal_rainfall_mm, mean_temp_C, max_temp_C, min_temp_C, radiation_MJ_m2_day, humidity_%, eto_mm
- irrigation_system, irrigation_events, irrigation_total_mm, days_under_water_stress, days_over_water_stress
- fertilizer_* (N/P/K at pre, set, maturity)
- disease_pressure, major_event
- ndvi_vegetative, ndvi_flowering, ndvi_harvest
- soil_moisture_30cm_weekly (semicolon-separated series)
- trees_per_ha
- **yield_kg_per_ha** (target), **yield_kg_per_tree**

## Quick start
1. `pip install -r requirements.txt`
2. Run notebooks in order:
   - `notebooks/01_eda.ipynb`
   - `notebooks/02_modeling.ipynb`

## License
This dataset is synthetic; use freely for research and demonstration. Please do not claim it as real field measurements.
