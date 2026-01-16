# Syracuse 911 Demand Explorer: Calls-for-Service and Parking Patterns (2023–Present)

[![Open in GitHub](https://img.shields.io/badge/Repo-Task__09__Syracuse__911__Demand__Explorer-blue)](https://github.com/gauravyadav-git/Task_09_Syracuse_911_Demand_Explorer)

---

## Project Overview

This project analyzes Syracuse Police Department calls‑for‑service and parking violations (2023–present) to understand when and where police demand is highest and how parking enforcement patterns compare.[file:145] Processed, analysis‑ready tables feed into a Power BI dashboard for interactive exploration.[file:145]

---

## Repository Structure

- `notebooks/`  
  - `phase2_exploration.ipynb` – Week 3–4 EDA and visualizations.[file:183]  
  - `phase3_pipeline.ipynb` – Week 5–6 reproducible data pipeline.

- `data_raw/`  
  - Raw CSVs downloaded from the Syracuse Open Data Portal and already committed for this project.

- `data_processed/`  
  - `crime_clean.parquet`, `crime_clean.csv` – cleaned, feature‑engineered calls‑for‑service data.  
  - `parking_clean.parquet`, `parking_clean.csv` – cleaned parking violations data.

- `figures/`  
  - PNG exports of key charts (calls by hour, calls by day of week, top incident types, parking tickets by month, etc.).

- `documentation/`  
  - Project proposal and Week‑6 architecture review.[file:186]

---

## Data Sources

- **Calls‑for‑Service (2023–2025)** – includes `DATEEND`, `TIMESTART`, `TIMEEND`, `ADDRESS`, `CODE_DEFINED`, `LarcenyCode`, `Arrest`, `LAT`, `LONG`.[file:145]  
- **Parking Violations (2023–present)** – includes `ticket_number`, `issued_date`, `location`, `description`, `status`, `amount`, `LAT`, `LONG`.[file:145]  

These raw CSVs are stored in `data_raw/` and serve as the single source of truth for the pipeline.

---

## How to Run the Pipeline

1. **Clone the repo**

   ```bash
   git clone https://github.com/gauravyadav-git/Task_09_Syracuse_911_Demand_Explorer.git
   cd Task_09_Syracuse_911_Demand_Explorer
