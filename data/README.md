
# Data inventory & reproducibility

The notebook expects `data/hcm_multimodal_dataset_v3.xlsx` with worksheets including `multimodal_trip_samples` (500 records, 50 fields in notebook output) and `grab_traffic_segments`. This training workbook **was not among the uploaded source documents**. The repository intentionally does not synthesize or fabricate it.

The archived notebook's data preparation and model comparison can be inspected through saved outputs, but re-training requires the original workbook. The project report describes a scoped collection of traffic/bus/metro segments; do not infer that full live bus/metro feed datasets are included here.

**Predicted label:** `recommended_total_cost_vnd`. **Inputs:** distance, traffic level, bus availability, metro availability, passenger count, time-of-day slot, walking distance to transit, Grab pickup ETA and nearby driver distance. Review the code before substituting another dataset, and audit source rights and data provenance.

**Privacy:** Avoid committing individual trip logs, private geolocation histories, API credentials or restricted transport provider data.
