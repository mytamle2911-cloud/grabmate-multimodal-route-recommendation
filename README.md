# GrabMate | AI-Assisted Multimodal Journey Recommendation

**Bridging first-mile and last-mile gaps through geospatial data, route comparison and applied machine learning.**

**Role:** Project Leader & Lead MVP Developer  
**Team:** 6 members 
**Delivery:** CPMAI × Agile · 10-week project plan · Four 2-week sprints  
**Focus:** Map Operations · Geospatial Data · Route Recommendation · Data Analytics · Project Management

[**Project Management Artifacts**](docs/project-management/README.md) · [**Original Landing Page**](https://bit.ly/486Xamc)

> **Independent student project.** GrabMate is a university-developed **concept and proof of concept**, not an official Grab feature, partnership, live integration or production release. Operational KPIs and financial projections are *proposed scenarios*, not measured Grab business outcomes.

## Project snapshot

| Dimension | What we built / documented |
| --- | --- |
| **The challenge** | Fragmented planning when travelers combine ride-hailing, bus and metro, especially for first-/last-mile connections |
| **The solution** | An interactive Python MVP that resolves locations, finds transit connection options, estimates travel time and cost, and compares multimodal journeys |
| **Geospatial layer** | Location aliases, OpenStreetMap **Nominatim** geocoding, proximity-based stop selection and route-related distance calculations |
| **Data & ML** | A coursework dataset of **500 multimodal trip samples**; preprocessing and comparison of five model families for predicted trip **cost** |
| **Saved model result** | **RandomForest_Deep: R² 0.931; MAE 495.68 VND; MAPE 6.74%** on the notebook's held-out sample |
| **Delivery management** | Work Breakdown Structure, RACI/project coordination, sprint planning, communication plan, risk management, launch OKRs and closeout documentation |

*The model metrics above come from **saved notebook output**, not a fresh training run. The original training workbook was not provided with the project archive. They are not production routing, ETA or user-impact metrics.*

---

## 1. Problem discovery: making multimodal travel usable

Urban commuters may combine a short ride-hailing trip with bus or metro to reduce the cost of a longer journey. But planning across modes introduces practical problems:

- **First-/last-mile gaps:** Reaching and leaving stations may require additional transport.
- **Fragmented route information:** Users must compare separate services, transfers and estimated fares.
- **Uncertain time–cost trade-offs:** The cheapest journey is not always the fastest or most convenient.
- **Location and data consistency:** Stop coverage, address matching and transport conditions affect whether a suggested route makes sense.

**Product question:** *How might we help commuters compare ride-hailing-only and Grab + public transport alternatives within a single journey-planning experience?*

**Project scope:** A 2025 Ho Chi Minh City study centered on Metro Line 1 and connecting bus access, with selected routes and UEH-related demonstration locations. The aim was to validate a **multimodal route-recommendation concept**, rather than reproduce a citywide navigation platform.

[Read problem discovery →](research/Problem_Discovery.md) · [Read full analysis →](docs/GrabMate_Final_Report.pdf)

## 2. The solution: a route recommendation MVP

GrabMate explores a trip from origin to destination by generating and comparing candidate journeys across ride-hailing and public transit.

```text
Origin + destination
        │
        ▼
Location resolution
(known aliases / OSM Nominatim)
        │
        ▼
Nearby transit-stop identification
        │
        ▼
Candidate journey generation
(Grab only / Grab + Bus / Grab + Metro)
        │
        ▼
Travel-time and fare estimation
(rule-based time; ML-assisted cost where available)
        │
        ▼
Option comparison + recommendation
        │
        ▼
Route and transfer information
```

### What I implemented in the MVP

| Capability | Implementation approach | Operational relevance |
| --- | --- | --- |
| **Address input & geocoding** | Resolve supported local aliases or request coordinates using OSM/Nominatim | Turning user-entered locations into usable spatial inputs |
| **Transit-stop matching** | Identify nearby bus/metro options and build possible connections | Stop proximity and first-/last-mile accessibility |
| **Route generation** | Compare ride-hailing-only and supported combinations with public transit | Translating transport networks into feasible user choices |
| **Journey estimation** | Estimate travel time using distance/mode assumptions; estimate costs with a trained Random Forest when available or a fallback rule | Time/cost trade-offs and graceful fallback |
| **Recommendations** | Apply prototype selection/comparison logic to candidate journeys | Decision support, rather than showing an unranked list |
| **Interactive demonstration** | Run a Python notebook/console-based planner and walkthrough | End-to-end proof of concept from data to user interaction |

**Technical boundary:** The prototype does **not** make actual Grab bookings or payments. It does **not** demonstrate verified real-time bus/metro feeds or production-grade routing. Traffic conditions are simulated in the prototype, and travel times are rule-based estimates.

**Demo & source:** [Video walkthrough](prototype/GrabMate_Demo.mp4) · [Original implementation notebook](analysis/GrabMate_EDA_Modeling_Prototype.ipynb) · [MVP notes](prototype/README.md)

## 3. My contributions: project leadership + hands-on development

As **Project Leader and Lead MVP Developer**, I coordinated the six-member team while directly owning key technical and product deliverables. The project's [Work Breakdown Structure](docs/project-management/Work_Breakdown_Structure.pdf) identifies my assigned work:

| Workstream | My contribution | Evidence |
| --- | --- | --- |
| **Project leadership & delivery** | Coordinated milestones, task allocation and cross-workstream delivery through CPMAI × Agile | [WBS](docs/project-management/Work_Breakdown_Structure.pdf), [PM hub](docs/project-management/README.md) |
| **Data understanding** | Prepared the data-source description, structure and dictionary workstream | [WBS](docs/project-management/Work_Breakdown_Structure.pdf), [report](docs/GrabMate_Final_Report.pdf) |
| **Product design** | Owned interface mockups for the proposed route-planning experience | [WBS](docs/project-management/Work_Breakdown_Structure.pdf) |
| **ML development** | Built the data-preparation and baseline-modeling workstream | [Source notebook](analysis/GrabMate_EDA_Modeling_Prototype.ipynb) |
| **Model evaluation** | Owned deeper model comparisons and explainability/SHAP assessment | [Model evaluation](results/Model_Evaluation.md), [notebook](analysis/GrabMate_EDA_Modeling_Prototype.ipynb) |
| **Lead MVP development** | Built and integrated the interactive prototype: location resolution, multimodal options, time/cost calculation and recommendations | [Notebook](analysis/GrabMate_EDA_Modeling_Prototype.ipynb), [demo](prototype/GrabMate_Demo.mp4) |

**Leadership did not mean claiming everyone's work.** Business-environment analysis, financial evaluation, later model tuning, operational rollout planning and visual presentation also had other named team owners. My role was to coordinate the project and deliver the MVP's primary technical implementation.

## 4. Geospatial data & map-operations thinking

The project connects three problems that are important in transportation operations:

**Location accuracy.** Origin/destination names must resolve to usable coordinates. The MVP combines predefined location aliases with Nominatim geocoding, while the project documents note the risk of outdated administrative names and inconsistent address mapping.

**Network and stop coverage.** A transit recommendation depends on nearby stops and the ability to connect separate legs. The prototype explores proximity-based stop matching and multimodal alternatives, within a **limited reference network**.

**Data reliability.** A route can look attractive mathematically but become impractical if its transport data, availability or travel times are wrong. The project [risk management plan](docs/project-management/Risk_Management_Plan.pdf) therefore identifies delayed transit updates, peak-hour ETA errors and limited trip samples as risks. Proposed mitigations include fallback estimates, broader validation and improved data synchronization; these are **plans**, not evidence of live partner integration.

**Operational takeaway:** A route-recommendation feature needs more than an ML score. Reliable geocoding, stop coverage, data freshness, usable fallbacks and monitoring are central to making a transport recommendation trustworthy.

## 5. Data analytics & machine learning

### Data pipeline

The notebook covers **exploratory analysis → feature preparation → model comparison → explanation and fairness review → interactive MVP**. The uploaded notebook references a multimodal trip dataset containing **500 sample records**. The original Excel training data are not in this repository, so the training outputs are preserved as project evidence but cannot be independently regenerated from the archive alone.

**Prediction target:** `recommended_total_cost_vnd` — recommended journey **cost**, in VND. This is **not an ETA prediction model**.

The model uses pre-trip attributes including trip distance, traffic level, availability of bus/metro, passenger count, time of day, walking distance to transit, pickup ETA and nearby driver distance. The notebook compares baseline and tree-based regressors using an 80/20 held-out split.

### Saved model comparison

| Model | MAE (VND) ↓ | MAPE ↓ | RMSE (VND) ↓ | R² ↑ |
| --- | ---: | ---: | ---: | ---: |
| **RandomForest_Deep** | **495.68** | **6.74%** | **569.65** | **0.931** |
| Ridge Regression | 562.58 | 6.93% | 860.35 | 0.843 |
| Linear Regression | 564.35 | 6.94% | 866.33 | 0.841 |
| Dummy baseline | 784.17 | 8.54% | 2,173.43 | -0.000 |
| Decision Tree | 958.25 | 11.06% | 1,958.15 | 0.188 |

**Why Random Forest?** Journey cost can depend on nonlinear interactions between distance, transport availability and traffic conditions. In the saved offline comparison, Random Forest yielded the lowest errors among the reported candidates. The notebook also includes **SHAP-based model explanation** and a **bias/fairness audit**.

**How I interpret the result:** R² = 0.931 is a promising *in-sample-study holdout* result for the cost-prediction proof of concept. It does **not** prove reliable fare estimates on new routes or actual citywide travel, and it does **not** establish ETA accuracy. Real-world testing would need independent trip observations, time-based validation, geographic holdouts, model-drift checks and route feasibility audits.

[Model evaluation details →](results/Model_Evaluation.md) · [Modeling methodology →](models/README.md) · [Evidence and limitations →](results/Evidence_and_Limitations.md)

## 6. Project management: from scope to handoff

I managed the project using **CPMAI for the AI lifecycle** and an **Agile-inspired, four-sprint delivery plan**. We used artifacts to make scope, dependencies, owners, risk and proposed success criteria explicit.

### Sprint delivery plan

| Sprint | Focus | Main planned deliverables |
| --- | --- | --- |
| **1 · Weeks 2–3** | Understand the business problem and data | AI Canvas, market/business analysis, data inventory, mockups |
| **2 · Weeks 4–5** | Prepare data and establish baselines | EDA, preprocessing, baseline models and first evaluation |
| **3 · Weeks 6–7** | Improve and evaluate the solution | Comparative model metrics, SHAP, business case and deployment planning |
| **4 · Weeks 8–9** | Demonstrate and communicate | Interactive MVP, demo video, presentation and final report |

The four two-week sprints sit inside the broader ten-week project schedule, which also includes setup and wrap-up.

### Management artifacts

| Artifact | How it supported the project |
| --- | --- |
| [**Work Breakdown Structure**](docs/project-management/Work_Breakdown_Structure.pdf) | Milestones, deliverables, time estimates and clear accountability by team member |
| [**Project OKRs**](docs/project-management/Project_OKRs.pdf) | Proposed measurable targets for user adoption, route experience and operational stability |
| [**Risk Management Plan**](docs/project-management/Risk_Management_Plan.pdf) | Identified risks around data latency, inaccurate recommendations, coverage and rollout; documented mitigation strategies |
| [**Communication Plan**](docs/project-management/Communication_Plan.pdf) | Defined intended stakeholder communications, responsible owners, channels and cadence |
| [**Project Closeout Report**](docs/project-management/Project_Closeout_Report.pdf) | Captured retrospective issues and proposed follow-up work, including address normalization and expanded validation |
| [**Business Evaluation**](docs/business/Business_Evaluation.xlsx) | Modeled potential financial viability under project assumptions |

**Evidence distinction:** These documents demonstrate **project planning and management work**. Proposed user-adoption targets, external stakeholder interactions, API synchronization, ROI and launch outcomes should not be interpreted as independently verified achievements.

[View the project-management documentation hub →](docs/project-management/README.md)

## 7. Results, limitations & decisions

### What the project demonstrated

- Built a working **notebook-based multimodal route-comparison prototype** connecting location inputs to candidate journeys and recommendations.
- Applied spatial lookup and transit-stop matching as part of route generation.
- Compared regression approaches for **journey cost prediction** and documented an explainability/fairness workflow.
- Delivered a full academic project package: business analysis, MVP, model evaluation, financial scenarios and project-management controls.

### What remains unvalidated

- **Real-time operations:** No verified live Grab/transit API integration, live booking, production monitoring or citywide service coverage.
- **Data reproducibility:** The original dataset and trained `model.pkl` were not supplied. Notebook outputs are retained, but full end-to-end retraining requires those inputs.
- **ETA accuracy:** Trip durations are estimated using rules/assumptions rather than an evaluated ETA-specific ML model.
- **Routing validation:** Stop data, transfer feasibility, address freshness and unexpected service disruptions need stronger real-world checks.
- **Business outcomes:** Forecasts or targets such as shorter trips, adoption, uptime and financial return are **not measured production results**. The draft closeout document includes some inconsistent figures and dates relative to other project materials.

### Next iteration I would prioritize

1. **Improve map-data quality:** Build an address-normalization layer, versioned stop/route records and validation checks for missing, duplicate or outdated locations.
2. **Validate route feasibility:** Check transfer walking distances, timetables and availability; add clearer fallbacks when data are incomplete.
3. **Evaluate using real journeys:** Acquire permissioned real trip data; use location/time holdouts to assess cost error, travel-time error and recommendation quality separately.
4. **Operationalize responsibly:** Track geocoding failure rate, route availability, data freshness, prediction drift and user-reported issues before expanding coverage.
5. **Package the demo:** Separate geocoding, route-generation, cost estimation and recommendation logic into tested modules behind a simple UI/API.

## 8. Explore the repository

```text
grabmate-multimodal-route-recommendation/
├── README.md
├── assets/
│   └── grabmate-cover.png
├── research/
│   └── Problem_Discovery.md
├── data/
│   └── README.md                   # Inventory and missing-source note
├── analysis/
│   └── GrabMate_EDA_Modeling_Prototype.ipynb
├── models/
│   └── README.md                   # Cost-model approach
├── prototype/
│   ├── GrabMate_Demo.mp4
│   └── README.md
├── results/
│   ├── Model_Evaluation.md
│   └── Evidence_and_Limitations.md
├── docs/
│   ├── GrabMate_Final_Report.pdf
│   ├── GrabMate_Presentation.pdf
│   ├── business/
│   │   └── Business_Evaluation.xlsx
│   └── project-management/
│       ├── README.md
│       ├── Work_Breakdown_Structure.pdf
│       ├── Project_OKRs.pdf
│       ├── Risk_Management_Plan.pdf
│       ├── Communication_Plan.pdf
│       └── Project_Closeout_Report.pdf
└── requirements.txt
```

### Suggested review path

1. **See the product:** [Demo video](prototype/GrabMate_Demo.mp4) → [slides](docs/GrabMate_Presentation.pdf).
2. **Inspect my development work:** [Notebook](analysis/GrabMate_EDA_Modeling_Prototype.ipynb) → [model evaluation](results/Model_Evaluation.md).
3. **Review my management work:** [WBS](docs/project-management/Work_Breakdown_Structure.pdf) → [risk plan](docs/project-management/Risk_Management_Plan.pdf) → [PM hub](docs/project-management/README.md).
4. **Read the research:** [Full report](docs/GrabMate_Final_Report.pdf) → [business evaluation](docs/business/Business_Evaluation.xlsx).

### Reproducing the notebook

The repository includes the original project notebook and saved outputs, **not** the complete original training dataset. To retrain, supply the missing `data/hcm_multimodal_dataset_v3.xlsx`, install dependencies from `requirements.txt`, and run the notebook cells in sequence to generate the fitted model. The interactive prototype can use its rule-based fare fallback if no trained model file is present. Nominatim requests require network access. This is **not** a ready-to-deploy web or mobile application.

---

**University of Economics Ho Chi Minh City (UEH)** · AI Project · Group 2 · November 2025  
**Portfolio emphasis:** Geospatial Data Processing · Multimodal Route Logic · Data Quality · Applied ML · Project Delivery

*GrabMate is an independent educational concept and is not affiliated with, sponsored by or endorsed by Grab.*
