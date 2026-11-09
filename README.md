# QGI 3.0 — Standalone Streamlit Prototype (2024)

> [!IMPORTANT]
> **Historical Archive (`QGI v3.0`, 2024):** This repository contains the standalone multi-page Streamlit prototype of **Quantitative Geopolitical Intelligence (QGI)** developed in January–February 2024. Active production development now resides in **QGI 7.0** at [`AminAlAit/qgi`](https://github.com/AminAlAit/qgi) (Live at [qgintelligence.com](https://qgintelligence.com)).

[![Python](https://img.shields.io/badge/Python-3.10-3776AB?style=flat-square&logo=python&logoColor=white)](https://www.python.org/)
[![Framework](https://img.shields.io/badge/Streamlit-1.36.0-FF4B4B?style=flat-square&logo=streamlit&logoColor=white)](https://streamlit.io/)
[![Status](https://img.shields.io/badge/Status-QGI_3.0_Historical_Prototype-blue?style=flat-square)](#)
[![License](https://img.shields.io/badge/License-Apache_2.0-green?style=flat-square)](LICENSE)

## QGI Generational Lineage (`v1.0` → `v7.0`)

| Generation | Period | Architecture & Milestone | Repository |
|---|---|---|---|
| **QGI 1.0** | Mar–Oct 2023 | Initial Pairwise Country Correlation Engine & Streamlit Prototype | `AminAlAit/trojan`, `AminAlAit/trojan-streamlit` |
| **QGI 2.0** | Nov 2023 | Soft Power & Institutional Composite Index Prototype | `AminAlAit/trojan-2.0` |
| **QGI 3.0** | Jan–Feb 2024 | Standalone Multi-Page Streamlit Analytical Terminal | [`AminAlAit/qgi-streamlit`](https://github.com/AminAlAit/qgi-streamlit) |
| **QGI 4.0** | Feb–Sep 2025 | Local SCDI Formalization, MySQL→Parquet Engine (Pipelines A–E) & X Bot v1 | `AminAlAit/qgi-4.0` |
| **QGI 5.0** | Sep 2025–Mar 2026 | First-Generation AWS Cloud Migration (Decoupled Lambda & Batch Microservices) | `AminAlAit/qgi-pipeline-a/b/c-*` |
| **QGI 6.0** | Mar–Aug 2026 | 7-Repo Multi-Account AWS Cloud (14.3B FFT Correlations) & Trajectory Engine (42 Models) | `AminAlAit/qgi-{aws-tf,infra,pipeline,data,ml,frontend}` |
| **QGI 7.0** | Oct 2026–Present | **Unified Public Monorepo & Sovereign IP Vault (Active Production)** | [`AminAlAit/qgi`](https://github.com/AminAlAit/qgi) & `AminAlAit/qgi-docs` |

---

## The Origin Story

In January 2024, I wanted to answer a fundamental quantitative question: **Do historical macroeconomic and geopolitical trajectories across nations repeat with measurable cross-correlation?**

When an emerging economy experiences a specific combination of debt-to-GDP spikes, currency devaluations, and demographic shifts, can we algorithmically match that multi-variable curve against historical precedents (e.g., Latin America in the 1980s, Southeast Asia in 1997, or Southern Europe in 2011) to understand what followed?

This repository was my first standalone interactive terminal built around that engine. Over a four-week sprint, I pulled together historical datasets from the World Bank and UN statistical divisions, built rolling cross-correlation routines in NumPy and SciPy, and wrapped the entire workflow in a multi-page Streamlit interface so hypotheses could be explored in real time.

---

## What This Prototype Does

1. **Cross-National Indicator Matching:** Select a target country and a historical time window, then query multi-indicator time series across 100+ nations.
2. **Lagged Correlation Engine:** Compute lead-lag correlation coefficients across temporal series to identify preceding and trailing indicators.
3. **Interactive Visual Exploration:** Render dynamic ECharts and Plotly charts directly inside Streamlit with configurable normalization and windowing filters.

---

## What I Learned (and Why We Outgrew It)

This prototype accomplished exactly what a prototype should: it validated the analytical concept and surfaced the engineering bottlenecks of scaling time-series analysis in a single Python process.

* **In-Memory Compute Ceilings:** Running all-to-all cross-correlations across hundreds of time series with varying sample frequencies on a single thread caused severe CPU and memory bottlenecks as dataset sizes grew.
* **The Monolith Problem:** Tightly coupling data ingestion, statistical computation, and front-end rendering inside a single Streamlit script meant that UI re-renders frequently triggered redundant compute cycles.
* **Data Freshness & Pipeline Fragility:** Relying on local CSVs and ad-hoc fetch scripts lacked schema validation, data versioning, and automated reconciliation.

These hard lessons directly informed the subsequent generations (QGI 4.0 through **QGI 7.0** at [`AminAlAit/qgi`](https://github.com/AminAlAit/qgi)), where compute, storage, and visualization were completely decoupled across a 5-account AWS organization, a 14.3B-correlation FFT Batch engine, a 42-model Trajectory Engine, and a zero-database Next.js 16 frontend.

---

## Running the Prototype Locally

The codebase has been cleaned and pinned to Python 3.10 to ensure it boots cleanly on modern systems without dependency breakage.

### Quickstart

```bash
git clone https://github.com/AminAlAit/qgi-streamlit.git
cd qgi-streamlit
python -m venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate
pip install --upgrade pip
pip install -r requirements.txt
streamlit run app.py
```

Open your browser at `http://localhost:8501` to explore the original interface.

---

## Repository Structure

```text
qgi-streamlit/
├── data/               # Curated historical sample indicators & country pattern CSVs
├── constant/           # Portable path constants, sector mappings, and index metadata
├── database/           # Pattern ranking and country lookup helpers
├── pages/              # Streamlit multi-page views (Base, Patterns, Events, FAQ, Contact)
├── plotting/           # Interactive ECharts and timeline chart wrappers
├── utils/              # Cross-correlation, filtering, and time-series transformation logic
├── app.py              # Main Streamlit application entry point
├── requirements.txt    # Pinned, reproducible runtime dependencies
├── .gitignore          # Clean environment and OS exclusions
└── README.md           # Historical context and run instructions
```

---

## License

This historical codebase is released under the [Apache 2.0 License](LICENSE).