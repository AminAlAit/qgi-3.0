# QGI 3.0 — Multi-Page Streamlit Analytical Terminal (2024)

**Generation 3.0 of 7.0** · Originally developed under **`AminAlAit/qgi`** (2024), **`AminAlAit/qgi-streamlit`**, and **`AminAlAit/qgi-local`** · **Current Production Platform:** [**`AminAlAit/qgi` (QGI 7.0)**](https://github.com/AminAlAit/qgi) ([qgintelligence.com](https://qgintelligence.com))

---

## Overview

In early 2024, the project dropped the internal `trojan` codename and became **Quantitative Geopolitical Intelligence (QGI)**. **QGI 3.0** (`192` commits) was the first full-featured interactive analytical terminal, built in Python with **Streamlit**, **Plotly**, and a relational **SQLite/MySQL** query layer (`database/db_manager.py`).

It connected historical bilateral macroeconomic indicator alignments (`pages/patterns.py`) directly to curated geopolitical and historical shock events (`pages/events.py`), allowing an analyst to select a country, inspect which historical peers shared its multi-indicator trajectory, and examine what events followed those historical precedents.

---

## Architecture & Key Modules

- **`app.py` & `pages/` (Multi-Page Streamlit Application):**
  - `pages/patterns.py`: Interactive bilateral pattern browser filtering country pairs by indicator overlap, lag offset, and correlation strength.
  - `pages/events.py`: Historical geopolitical event overlay linking macro-trajectory matches to real-world political and economic inflection points.
- **`database/db_manager.py` (Relational Data Access Layer):**
  - Replaced the flat `.csv`/`.pkl` directory scans of QGI 1.0–2.0 with indexed relational queries (`get_country_b_counts_for_country_a()`, `get_alpha2_by_name()`, bilateral pattern joins).
- **`plotting/plotting.py` (Interactive Dual-Axis Trajectory Charts):**
  - Built reusable Plotly time-series overlays comparing Country A's window $[t_1, t_2]$ against Country B's lagged historical window $[t_1 - \tau, t_2 - \tau]$ with normalized axes and event markers.
- **`utils/` & `data/`:**
  - ISO country code normalization, flag assets, and pre-indexed indicator metadata.
- **`qgi-local/` (Merged Companion Stub):**
  - Preserves the 2024 `AminAlAit/qgi-local` companion repository (also preserved on branch `qgi-local/main`).

---

## Repository Structure

```text
qgi-3.0/
├── app.py                         # Streamlit multi-page application entry point
├── pages/
│   ├── patterns.py                # Bilateral macroeconomic pattern explorer
│   └── events.py                  # Geopolitical event precedent view
├── database/
│   └── db_manager.py              # SQLite/MySQL query layer & country aggregation
├── plotting/
│   └── plotting.py                # Interactive Plotly dual-country trajectory charts
├── data/                          # Curated World Bank indicator & country reference tables
├── utils/                         # Formatting, caching & ISO-3166 helpers
├── qgi-local/                     # Merged commit history of companion repo AminAlAit/qgi-local
└── requirements.txt               # Python runtime dependencies
```

---

## Why We Outgrew QGI 3.0

- **Similarity Metric Rigor:** Simple linear correlation missed non-linear phase shifts and rank-order monotonic relationships across economies of different scales. This led to formulating the composite **SCDI (Spearman + Lagged Cross-Correlation + Dynamic Time Warping)** metric in **QGI 4.0**.
- **Storage & Compute Ceiling:** Querying millions of multi-indicator combinations from a local relational database hit I/O limits, motivating the migration to partitioned **Apache Parquet** in **QGI 4.0** and distributed **AWS Batch + S3** in **QGI 5.0–7.0**.

---

## QGI Generational Roadmap (`v1.0` → `v7.0`)

| Generation | Year | Repository | Original Name(s) | Architectural Milestone |
| :--- | :--- | :--- | :--- | :--- |
| **QGI 1.0** | 2023 | [`AminAlAit/qgi-1.0`](https://github.com/AminAlAit/qgi-1.0) | `trojan`, `trojan-streamlit` | Initial pairwise country correlation engine & first Streamlit UI |
| **QGI 2.0** | 2023 | [`AminAlAit/qgi-2.0`](https://github.com/AminAlAit/qgi-2.0) | `trojan-2.0` | Poetry-packaged ETLP pipeline, `Index` OOP hierarchy & STUMPY matrix profiles |
| **QGI 3.0** *(Here)* | 2024 | **`AminAlAit/qgi-3.0`** | `qgi` (2024), `qgi-streamlit`, `qgi-local` | Multi-page Streamlit analytical terminal backed by relational SQLite/MySQL queries |
| **QGI 4.0** | 2025 | [`AminAlAit/qgi-4.0`](https://github.com/AminAlAit/qgi-4.0) | `qgi-4.0` | Formalization of the SCDI metric (Spearman + Cross-Correlation + DTW), Pipelines A–E & X Bot v1 |
| **QGI 5.0** | 2025–2026 | [`AminAlAit/qgi-5.0`](https://github.com/AminAlAit/qgi-5.0) | `qgi-pipeline-a/b/c` | First AWS cloud migration: Serverless Lambda ETL, Dockerized AWS Batch FFT worker & Athena CTAS |
| **QGI 6.0** | 2026 | `AminAlAit/qgi-6.0` | `qgi-aws-tf`, `qgi-infra`, `qgi-pipeline`, `qgi-data`, `qgi-ml`, `qgi-frontend`, `qgi-docs` | 4-account AWS Organization (14.3B FFT correlations), 42-model Trajectory Engine & Next.js 16 terminal |
| **QGI 7.0** *(Active)* | 2026–Present | [**`AminAlAit/qgi`**](https://github.com/AminAlAit/qgi) | `qgi`, `qgi-docs` | Unified production monorepo & live analytical terminal at [qgintelligence.com](https://qgintelligence.com) |
