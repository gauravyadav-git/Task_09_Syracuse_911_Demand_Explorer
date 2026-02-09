# Syracuse 911 Demand Explorer: Calls-for-Service and Parking Patterns (2023–Present)

[![Open in GitHub](https://img.shields.io/badge/Repo-Task__09__Syracuse__911__Demand__Explorer-blue)](https://github.com/gauravyadav-git/Task_09_Syracuse_911_Demand_Explorer)

---

## Project Overview

This project analyzes Syracuse Police Department calls‑for‑service and parking violations (2023–present) to understand when and where police demand is highest and how parking enforcement patterns compare. Processed, analysis‑ready tables feed into a Power BI dashboard for interactive exploration.

---

## Repository Structure

- `notebooks/`  
  - `phase2_exploration.ipynb` – Week 3–4 EDA and visualizations.
  - `phase3_pipeline.ipynb` – Week 5–6 reproducible data pipeline.

- `data_raw/`  
  - Raw CSVs downloaded from the Syracuse Open Data Portal and already committed for this project.

- `data_processed/`  
  - `crime_clean.parquet`, `crime_clean.csv` – cleaned, feature‑engineered calls‑for‑service data.  
  - `parking_clean.parquet`, `parking_clean.csv` – cleaned parking violations data.

- `figures/`  
  - PNG exports of key charts (calls by hour, calls by day of week, top incident types, parking tickets by month, etc.).

- `documentation/`  
  - Project proposal and Week‑6 architecture review.

---

## Data Sources

- **Calls‑for‑Service (2023–2025)** – includes `DATEEND`, `TIMESTART`, `TIMEEND`, `ADDRESS`, `CODE_DEFINED`, `LarcenyCode`, `Arrest`, `LAT`, `LONG`. 
- **Parking Violations (2023–present)** – includes `ticket_number`, `issued_date`, `location`, `description`, `status`, `amount`, `LAT`, `LONG`.

These raw CSVs are stored in `data_raw/` and serve as the single source of truth for the pipeline.

---

## How to Run the Pipeline

1. **Clone the repo**

   ```bash
   git clone https://github.com/gauravyadav-git/Task_09_Syracuse_911_Demand_Explorer.git
   cd Task_09_Syracuse_911_Demand_Explorer

2. **(Optional) Create and activate a virtual environment**

   ```bash
   python -m venv venv
   source venv/bin/activate   # Windows: venv\Scripts\activate

3. Install Dependencies

   ```bash
   pip install -r requirements.txt

4. Run the pipeline notebook
   Open Jupyter Lab/Notebook and execute:

    notebooks/phase3_pipeline.ipynb from top to bottom.

This will:

  Load raw CSVs from data_raw/.
  
  Clean and combine crime and parking data.
  
  Drop records with impossible future dates (e.g., year 2210) and invalid ticket amounts.
  
  Create derived fields (year, hour, dow, month for crime; date, month for parking).
  
  Run a small set of QA tests (date ranges, missingness, basic sanity checks).
  
  Save cleaned datasets to data_processed/ as both Parquet and CSV.
  
  Export key figures to figures/.

You can still open notebooks/phase2_exploration.ipynb if you want to see the earlier EDA workflow and intermediate visualizations.

Using the Outputs:

  For Python analysis – use crime_clean.parquet and parking_clean.parquet in data_processed/ for faster, type‑safe loading.
  
  For Power BI / Excel – connect directly to crime_clean.csv and parking_clean.csv in data_processed/ as the analysis‑ready fact tables.
  
  For reports/slides – use PNGs in figures/ (calls by hour/day, top incident types, parking by month, etc.).

## (Weeks 3–6):

Completed exploratory analysis and first‑round visualizations in phase2_exploration.ipynb using the raw CSVs.

Implemented a reproducible raw → clean → processed pipeline with basic tests in phase3_pipeline.ipynb.

Organized the repository into notebooks/, data_raw/, data_processed/, figures/, and documentation/ to match the Week‑6 architecture review.

Next steps include connecting the processed CSVs to Power BI, designing dashboard pages for calls‑for‑service and parking, and exploring optional LLM‑based narrative summaries with validation against underlying measures.

## Current Status (Through Week 10):

**Weeks 7-8 Complete:** Connected crime_clean.csv to Power BI Desktop; built data model (types, relationships); created initial overview page with hourly bar chart (13K total calls, avg 17.09/day, peak 05:00) and KPIs.

**Weeks 9-10 Complete:** Feature-complete crime dashboard:
- Hour x dow heatmap (Matrix visual + conditional formatting)
- Geospatial map (LAT/LONG bubbles sized by Total Calls measure=COUNTROWS, legend by DEFINED crime type)
- Line chart (calls by hour segmented by dow)
- Synced slicers (hour, month, dow); tooltips/trend lines

.pbix file: `powerbi/Syracuse_911_Demand_Explorer.pbix` (embedded screenshots in repo).

**Week 10 Milestone Achieved:** Interactive prototype ready for stakeholder review.

Next steps (Weeks 11-13): Parking violations page; cross-dataset relationships; TECHNICAL.md/METHODOLOGY.md; presentation deck for Syracuse Open Data showcase.

