# Evidence quality & document reconciliation

| Claim | Classification | What is supported |
| --- | --- | --- |
| Six-person team and project lead | Confirmed in the course report and WBS | Lead listed as Lê Thị Mỹ Tâm; PM on WBS |
| Lead MVP developer | User-reported contribution; aligned with WBS ownership | MVP/prototype and modeling deliverables assigned to lead |
| 500 records, 50 columns | Observed in supplied notebook output | Training sheet loaded; workbook not supplied |
| R²=0.931, MAE=495.68 VND | Saved offline evaluation output | **Cost prediction** test metric only |
| ETA R²≈0.588 | Earlier unverified description | Not substantiated as result by uploaded notebook |
| 15% trip time reduction, 20,000 beta users, 99.5% uptime | Planned OKRs | **Not actual outcomes** |
| ROI, IRR, NPV | Modeled scenario outputs | Business workbook and report use different figures; not verified commercial results |
| Live transit API synchronization, actual rider pilot | Appears as accomplishment in draft closeout | No production logs, API access evidence or pilot dataset was supplied |
| Sprint structure | Report and WBS | 10-week planning framework / four 2-week sprint blocks |

**Conflict:** The project closeout draft refers to launch success and commercial results (including ROI ~178%) while final report uses different financial assumptions (e.g., 71.38% three-year ROI), and timelines differ. Present financial figures as scenario exercises and use the final report / WBS for project scope, not as proof of production results.

**Non-reproducibility:** Training workbook and trained `model.pkl` are absent. Notebook depends on network geocoding and external Python packages. Source is archived with saved outputs for transparent review; do not describe it as fully reproducible.
