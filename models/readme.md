# ML modeling notes

The final modeling notebook compares Dummy, LinearRegression, Ridge, DecisionTree_Simple and RandomForest_Deep with a held-out 80/20 split (random_state=42). Numeric and categorical preprocessing is fitted inside a scikit-learn pipeline. The winning Random Forest model predicts **trip cost (VND)**, not ETA.

The saved training notebook shows RandomForest_Deep: MAE 495.68 VND, MAPE 6.74%, RMSE 569.65 VND, R² 0.931. These are **recorded notebook results**, not a fresh retraining or external validation.

At the end of the training cell the fitted pipeline is saved as `model.pkl`; this file is **not supplied**. The prototype cell attempts to load it and falls back to rule-based fare estimates if unavailable. The notebook also includes SHAP explanation and fairness exploration. Avoid equating scenario-generated fairness charts with real-world equity audits.

**Deployment gaps:** independent live-fare validation, time-split testing, transfer feasibility, network geocoding reliability, monitoring, operational security and a separately trained ETA model.
