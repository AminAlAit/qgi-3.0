# QGI 3.0 — Historical 2024 Streamlit Prototype

> **[Historical Archive — Generation 3.0 of 7.0]**
> This repository preserves **QGI 3.0** (2024), the first prototype to adopt the **Quantitative Geopolitical Intelligence (QGI)** name (qgi.py) and ship a multi-page Streamlit analytical interface over World Bank macroeconomic time series.
> - **Original Repository Names:** `AminAlAit/qgi` (2024), `AminAlAit/qgi-streamlit`, and `AminAlAit/qgi-local`
> - **Active Production Platform (QGI 7.0):** [**AminAlAit/qgi**](https://github.com/AminAlAit/qgi) ([qgintelligence.com](https://qgintelligence.com))

---

## Architectural Scope (2024)

- **Original Repository References:**
  - **`AminAlAit/qgi` (2024) / `AminAlAit/qgi-streamlit`:** Originally created as `AminAlAit/qgi` in 2024, renamed to `AminAlAit/qgi-streamlit` during the QGI 7.0 monorepo cutover, and canonically archived here as `AminAlAit/qgi-3.0`.
  - **`AminAlAit/qgi-local`:** Companion 2024 local workspace stub created alongside the QGI 3.0 transition.
- **Interactive Prototype (qgi.py, main.py):** Early Streamlit dashboard (st_pages/) for exploring bilateral macroeconomic indicator alignments (patternEngine.py, patternValidator.py, dataPrep.py).
- **Research Notebooks (NBs/):** Initial World Bank API extraction and indicator curation notebooks (world_bank_indicators.ipynb, country_profile_maker.ipynb, index_maker.ipynb, stocker_maker.ipynb).

---

## QGI Generational Lineage (1.0 – 7.0)

| Generation | Era | Canonical GitHub Repository | Original Repository Name(s) | Key Milestone |
| :--- | :--- | :--- | :--- | :--- |
| **QGI 1.0** | 2023 | `AminAlAit/qgi-1.0` | `trojan`, `trojan-streamlit` | Initial pairwise country correlation engine (countriesIndex.py, patternEngine.py) & first Streamlit prototype |
| **QGI 2.0** | 2023 | `AminAlAit/qgi-2.0` | `trojan-2.0` | Poetry-managed Soft Power & composite institutional index prototype |
| **QGI 3.0** | 2024 | `AminAlAit/qgi-3.0` | `qgi` (2024), `qgi-streamlit`, `qgi-local` | First public Quantitative Geopolitical Intelligence Streamlit prototype & World Bank notebook workflows |
| **QGI 4.0** | 2025 | `AminAlAit/qgi-4.0` | `qgi-4.0` | Formalization of SCDI (Spearman + Cross-Correlation + DTW), local MySQL-to-Parquet engine (Pipelines A–E), and X Bot v1 |
| **QGI 5.0** | 2025–2026 | `AminAlAit/qgi-5.0` | `qgi-pipeline-a-indicator-extractor`, `qgi-pipeline-b-scdi-finder`, `qgi-pipeline-c-pattern-synthesizer` | First AWS cloud migration: Serverless Lambda indicator extractor, Dockerized AWS Batch SCDI compute worker, and Lambda pattern synthesizer |
| **QGI 6.0** | 2026 | `AminAlAit/qgi-6.0` | `qgi-aws-tf`, `qgi-infra`, `qgi-pipeline`, `qgi-data`, `qgi-ml`, `qgi-frontend`, `qgi-docs` | 7-repo multi-account AWS cloud architecture (14.3B FFT correlations), Trajectory Engine (42 event models), and Next.js 16 terminal |
| **QGI 7.0 (Active)** | 2026–Present | [**AminAlAit/qgi**](https://github.com/AminAlAit/qgi) & `AminAlAit/qgi-docs` | `qgi`, `qgi-docs` | Unified polyglot production monorepo & live analytical terminal at [qgintelligence.com](https://qgintelligence.com) |