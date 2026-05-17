<h1 align="center">Quantium — Data Analytics Job Simulation</h1>

<p align="center">
  <strong>Virtual Work Experience · The Forage · April 2026</strong><br/>
  Real-world retail analytics work: customer segmentation, A/B testing, and strategic reporting
</p>

<p align="center">
  <img src="https://img.shields.io/badge/The%20Forage-Quantium-0A66C2?style=flat-square&logo=data:image/png;base64," alt="Forage">
  <img src="https://img.shields.io/badge/Python-3.x-3776AB?style=flat-square&logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/Jupyter-Notebook-F37626?style=flat-square&logo=jupyter&logoColor=white" alt="Jupyter">
  <img src="https://img.shields.io/badge/pandas-Data%20Analysis-150458?style=flat-square&logo=pandas&logoColor=white" alt="pandas">
  <img src="https://img.shields.io/badge/Status-Completed-28a745?style=flat-square" alt="Completed">
</p>

---

## Table of Contents

- [About This Simulation](#about-this-simulation)
- [Simulation Summary](#simulation-summary)
- [Business Problem](#business-problem)
- [Tasks Completed](#tasks-completed)
- [Key Results & Impact](#key-results--impact)
- [Tools & Technologies](#tools--technologies)
- [Repository Structure](#repository-structure)
- [Simulation-to-Real-World Mapping](#simulation-to-real-world-mapping)
- [Business Problems Solved](#business-problems-solved)
- [Analytical Thinking Developed](#analytical-thinking-developed)
- [How My Thinking Changed](#how-my-thinking-changed)
- [What I Would Do Differently](#what-i-would-do-differently)
- [Connect](#connect)

---

## About This Simulation

This repository documents my completion of the **Quantium Data Analytics Virtual Job Simulation** on [The Forage](https://www.theforage.com/simulations/quantium/data-analytics-rqkb) — a structured, company-designed program that replicates real analyst work at Quantium, a global leader in data science and AI founded in 2002.

The simulation placed me in Quantium's **Retail Analytics team**, working on a real client brief from a Category Manager at a major Australian supermarket chain. The work spanned three tasks: data preparation, A/B testing, and executive reporting — mirroring an actual analyst project lifecycle.

> **This is not a tutorial or course project.** It is a structured professional simulation with real datasets, real business questions, and model answers benchmarked against Quantium's internal analyst standards.

---

## Simulation Summary

| Detail | Info |
|---|---|
| **Company** | Quantium |
| **Programme** | Data Analytics Job Simulation |
| **Platform** | The Forage |
| **Duration** | ~5 hours (self-paced) |
| **Completed** | April 2026 |
| **Location** | Bengaluru, Karnataka, India |
| **Certificate** | [View Certificate](certificates/) |
| **Simulation Link** | [The Forage — Quantium Data Analytics](https://www.theforage.com/simulations/quantium/data-analytics-rqkb) |


---

## Business Problem

> *"Who are the customers buying chips, what is their purchasing behaviour, and did our trial store layout drive increased sales?"*

**Client:** Julia Chen, Category Manager — Chips  
**Stakeholder:** Zilinka (Analytics Manager, Quantium)  
**Dataset:** 264,836 chip transactions · 272 stores · Jul 2018 – Jun 2019

The client needed a data-driven recommendation to:
1. Identify which customer segments drive the most chip sales and why
2. Evaluate whether a new chip aisle layout trialled in 3 stores (77, 86, 88) should be rolled out chain-wide

---

## Tasks Completed

<details>
<summary><strong>Task 1 — Data Preparation & Customer Analytics</strong> &nbsp;✅</summary>

<br/>

**Objective:** Clean raw transaction and customer data, engineer features, define metrics, segment customers, and deliver a commercial recommendation.

**What I did:**
- Loaded and merged two raw CSV files: `QVI_transaction_data.csv` (264,836 rows × 8 cols) and `QVI_purchase_behaviour.csv` (72,637 rows × 3 cols)
- Identified and resolved a critical data type issue — `DATE` column stored as an Excel integer serial number, converted to `datetime` via `origin='1899-12-30'`
- Detected and flagged a non-chip product (`Old El Paso Salsa Dip`) mixed into the chip category
- Engineered two new features from `PROD_NAME`:
  - `PACK_SIZE` — extracted via regex `(\d+)g`
  - `BRAND` — extracted by splitting on gram pattern
- Merged datasets on `LYLTY_CARD_NBR` using a left join (preserving all transactions)
- Built a segment summary table with 3 metrics across 7 LIFESTAGE × 3 PREMIUM_CUSTOMER groups:
  - Total Sales, Customer Count, Avg Sales Per Customer
- Created 4 charts: Total Sales by Segment, Avg Spend Per Customer, Customer Count, Pack Size Preference

**Key finding:** Pack size is uniform at ~180g across all segments — strategy should focus on spend frequency and basket size, not pack variation.

</details>

<details>
<summary><strong>Task 2 — Experimentation & Uplift Testing</strong> &nbsp;✅</summary>

<br/>

**Objective:** Identify matched control stores for each trial store, run A/B comparison, test statistical significance, and recommend whether to roll out the new layout.

**What I did:**
- Calculated monthly store-level metrics: `TOTAL_SALES`, `NUM_CUSTOMERS`, `AVG_TXN_PER_CUSTOMER`
- Split data into pre-trial (Jul 2018 – Jan 2019) and trial (Feb – Apr 2019) periods
- Built a custom `find_control_store()` function that scored all 269 candidate stores using:
  - **Pearson correlation** — measures how similarly stores trend over time
  - **Normalised magnitude distance** — `1 - (distance - min) / (max - min)` — accounts for store size differences
  - Combined FINAL_SCORE averaged across 6 scores (3 metrics × 2 methods)
- Applied scaling factor to control stores before comparison (corrects for size gap between trial and control)
- Ran independent t-tests to assess statistical significance during the trial period

**Control store assignments:**

| Trial Store | Control Store | Match Score | Sales Corr. | Customer Corr. |
|:-----------:|:-------------:|:-----------:|:-----------:|:--------------:|
| Store 77 | Store 17 | 0.8177 | 0.8427 | 0.7473 |
| Store 86 | Store 138 | 0.8399 | 0.7599 | 0.7497 |
| Store 88 | Store 178 | 0.7488 | 0.7319 | 0.9395 |

</details>

<details>
<summary><strong>Task 3 — Analytics & Commercial Application</strong> &nbsp;✅</summary>

<br/>

**Objective:** Synthesise all findings into a boardroom-ready report for the Category Manager using the **Pyramid Principles** framework.

**What I did:**
- Built a 12-slide executive presentation following the Pyramid Principles structure (answer first, evidence second)
- Included executive summary with 4 headline KPIs, 4 data visualisation slides, trial results table, and ranked strategic recommendations
- Wrote a professional cover email to the client (Julia) summarising key findings
- Produced 5 XYZ-format resume bullet points anchored to real numbers from the analysis

**Deliverable:** `Quantium_Chip_Category_Report.pptx` — available in this repository

</details>

---

## Key Results & Impact

| Metric | Value |
|---|---|
| Total revenue analysed | $1.93M (Jul 2018 – Jun 2019) |
| Transactions processed | 264,836 |
| Stores analysed | 272 |
| Customer segments evaluated | 21 (7 lifestages × 3 premium tiers) |
| Highest value segment | Older Families — Budget ($168,363 total / $36.01 avg per customer) |
| Largest customer segment | Young Singles/Couples — Mainstream (8,088 customers) |
| Biggest growth gap | $16.52 avg spend gap between top and bottom segments |
| Best trial uplift | Store 86 vs Control 138 → **+14.2% sales uplift** |
| Trial outcome | Phased rollout recommended (Store 86 extend; Store 88 revert) |

---

## Tools & Technologies

| Category | Tools Used |
|---|---|
| **Language** | Python 3.x |
| **Data Manipulation** | pandas, NumPy |
| **Visualisation** | matplotlib, seaborn |
| **Statistical Testing** | scipy.stats (Pearson correlation, independent t-test) |
| **Environment** | Jupyter Notebook, VS Code |
| **Reporting** | PowerPoint (PptxGenJS), Pyramid Principles framework |
| **Version Control** | Git, GitHub |

**Python libraries used:**
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from scipy import stats
```

---

## Repository Structure

```plaintext
quantium-Data-Analytics-Job-Simulation/
│
├── Store Sale analysis/              # Task 1 — Data prep & customer analytics
│   └── task1_analysis.ipynb                       
│
├── Trial Analysis/                   # Task 2 — Experimentation & uplift testing
│   └── task2_trialStore_analysis.ipynb                       
│
├── Quantium_Chip_Category_Report.pptx  # Task 3 — ppt slides executive report
│
└── README.md                         # This file
```

---

## Simulation-to-Real-World Mapping

| Simulation Task | Real Analyst Equivalent |
|---|---|
| Clean and merge transaction + customer data | Data engineering / ETL preparation before analysis |
| Engineer PACK_SIZE and BRAND from raw text | Feature engineering in production analytics pipelines |
| Segment customers by LIFESTAGE × PREMIUM_CUSTOMER | Customer segmentation for retail planogram strategy |
| Build control store matching function | Propensity score matching / A/B test design in industry |
| Pearson correlation + magnitude scoring | Similarity metrics used in uplift modelling |
| Statistical significance testing (t-test) | Hypothesis testing in experiment evaluation |
| Pyramid Principles report for Category Manager | Consulting-style client deliverable / strategy deck |

---

## Business Problems Solved

**1. Who should Julia target to grow chip sales?**  
Analysis revealed Older Families (Budget) as highest value per customer ($36.01 avg) while Young Singles/Couples (Mainstream) represented the largest untapped volume (8,088 customers, only $19.49 avg spend). These are two fundamentally different strategic levers — retention vs. frequency growth.

**2. Does pack size strategy need to change by segment?**  
Pack size analysis across all 21 segments showed near-uniform preference at ~180g. This ruled out pack size differentiation as a strategic priority — freeing category strategy to focus entirely on promotion mechanics and placement.

**3. Should the new store layout be rolled out chain-wide?**  
No — not yet. Store 86 showed a commercially meaningful +14.2% uplift but with only 3 months of data, statistical significance (p < 0.05) was not reached for any store. Recommendation: extend Store 86 trial, revert Store 88 (which underperformed by -5%), and monitor Store 77.

---

## Analytical Thinking Developed

- **Separating volume from value** — A segment can have high total sales simply because it has many customers, not because each one spends a lot. Developed the habit of always examining both total sales AND avg spend per customer before drawing conclusions.

- **Control store selection rigour** — Choosing the "most similar" store requires more than eyeballing data. Built a scoring system combining trend similarity (correlation) and size similarity (magnitude) to make the matching defensible and repeatable.

- **Statistical vs. commercial significance** — A result can be commercially meaningful (e.g. +14.2% uplift = real revenue) while not yet statistically significant due to sample size. Learned to report both dimensions honestly rather than oversimplifying.

- **Communicating to non-technical stakeholders** — The Pyramid Principles framework forces you to lead with the answer, not the method. Restructured thinking from "here's what I found" to "here's what you should do, here's why."

---

## How My Thinking Changed

**Before:** Data analysis meant cleaning data, running functions, and producing charts.

**After:** Data analysis is a commercial conversation. Every chart exists to answer a specific business question. Every recommendation needs to be defensible with numbers. The code is the least important part of the deliverable — the reasoning behind it is what matters.

The moment that shifted my perspective: realising that Store 86 had a +14.2% uplift but p = 0.1987 — and understanding *why* that doesn't mean the trial failed, it means we need more data before betting the whole chain on it.

---

## What I Would Do Differently

- **Add time-series trend analysis to Task 1** — Monthly sales trends within segments would have revealed seasonality patterns useful for Julia's half-year planning
- **Apply confidence intervals to the trial results** — Rather than just p-values, showing 95% confidence intervals around the uplift estimates would have been more informative for the rollout decision
- **Automate the full pipeline** — Tasks 1 and 2 could be structured as a single reproducible pipeline rather than two separate notebooks

---

## Connect

<p>
  <a href="https://www.linkedin.com/in/manjunathareddyn/">
    <img src="https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=flat-square&logo=linkedin" alt="LinkedIn">
  </a>
  &nbsp;
  <a href="https://github.com/MrBeastGamerZz">
    <img src="https://img.shields.io/badge/GitHub-MrBeastGamerZz-181717?style=flat-square&logo=github" alt="GitHub">
  </a>
</p>

---

<p align="center">
  <sub>Completed as part of The Forage Virtual Work Experience Program · Quantium Data Analytics · April 2026</sub>
</p>
