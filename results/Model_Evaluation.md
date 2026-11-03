# Model evaluation — saved notebook results

| Model | MAE (VND) | MAPE | RMSE (VND) | R² |
| --- | ---: | ---: | ---: | ---: |
| RandomForest_Deep | 495.68 | 6.74% | 569.65 | 0.931 |
| Ridge | 562.58 | 6.93% | 860.35 | 0.843 |
| LinearRegression | 564.35 | 6.94% | 866.33 | 0.841 |
| Dummy | 784.17 | 8.54% | 2173.43 | -0.000 |
| DecisionTree_Simple | 958.25 | 11.06% | 1958.15 | 0.188 |

Source: rendered pandas results output saved in uploaded `SOURCE CODE` notebook, cell 2 (the second code cell). **Target**: `recommended_total_cost_vnd`, **not ETA**. Holdout 80/20. The original dataset is missing; results have not been independently reproduced in this repository.

No validated production ETA-error, faster-trip, retention, customer adoption or deployment impact numbers are demonstrated by this offline test.
