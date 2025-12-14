# Syracuse 911 Demand Explorer: Calls-for-Service and Parking Patterns (2023–Present)

## Project Overview
This project analyzes Syracuse Police Department calls-for-service data from 2023 to the present, with a secondary focus on parking violations over the same period.[file:145] The goal is to build an interactive Power BI dashboard that shows when and where police demand is highest, which incident types drive that demand, and how patterns vary across time and space.[file:145] A supplementary page will summarize parking violation patterns and, where meaningful, highlight overlaps with key calls-for-service hotspots.[file:145]

## Problem Statement
City officials, community groups, and residents often discuss “crime” and “safety” without an easy way to see how police demand is actually distributed by time, location, and call type.[file:145] This project addresses two main questions:[file:145]

- When and where is police demand highest in Syracuse, and what types of incidents drive that demand?  
- What do parking violation patterns look like, and do they cluster around similar places or times as certain calls-for-service?  

By providing transparent, interactive visuals, the dashboard aims to support data-informed decisions, align expectations, and ground public conversations in evidence.[file:145]

## Stakeholders / Target Audience
- Syracuse Police Department analysts and leadership  
- Neighborhood associations and residents  
- City planners and parking/transportation staff  
- Journalists and researchers[file:145]

## Data Sources
- **Calls-for-Service (2023, 2024, 2025–present):** Includes DATEEND, TIMESTART, TIMEEND, ADDRESS, CODE_DEFINED, LarcenyCode, Arrest, LAT, LONG fields.[file:145]  
- **Parking Violations (2023–present):** Includes ticket_number, issued_date, location, description, status, amount, LAT, LONG.[file:145]  
- **Optional context:** Neighborhood or council-district boundaries for aggregation and mapping, if they add clear value.[file:145]

## Technical Approach
- Use **Python and/or SQL** for initial exploratory data analysis and data quality checks (profiling, date ranges, missing values, summary statistics).[file:145]  
- Export clean, well-documented tables from Python/SQL.  
- Use **Power BI** (Power Query) for ETL, derived columns (hour, day of week, year, weekday/weekend), and aggregation at appropriate geographic units.[file:145]  
- Build a data model with calls-for-service and parking violations as fact tables and date/time, location, and incident type as dimension tables.[file:145]  
- Optionally use LLMs later for narrative summaries of dashboard views, with all generated statements validated against underlying measures.[file:145]

## Planned Dashboard Pages

### 1. Calls-for-Service (Primary)
- Time-of-day and day-of-week patterns  
- Distribution by incident type (CODE_DEFINED, LarcenyCode)  
- Geographic hotspots using LAT/LONG or aggregated areas  
- Arrest vs. non-arrest metrics by call type and time  
- Year-over-year trends (2023–2025)[file:145]

### 2. Parking Violations (Secondary)
- Ticket counts over time by violation description  
- Location and financial impact of fines  
- Simple comparisons between parking hotspots and calls-for-service hotspots, without overclaiming causal relationships[file:145]

## Success Criteria
The project will be successful if:[file:145]

- Non-technical users can answer basic questions such as “When are calls-for-service highest?” and “What types of incidents are most common in my area?” via the dashboard.  
- The dashboard clearly visualizes key calls-for-service patterns across time, place, and incident type, surfacing at least one meaningful, well-documented insight for SPD or community partners.  
- The parking page provides a clear view of parking patterns and, where possible, simple comparisons to calls-for-service hotspots.  
- Analyses are reproducible from documented code and transformations, and any narrative statements (including LLM-assisted ones) are validated against the underlying data.[file:145]

## Repository Structure (planned)
- `README.md` – project overview and usage  
- `data/` – **not committed**; local raw and processed data (access via portal)  
- `notebooks/` – Python/SQL EDA and exploration reports  
- `powerbi/` – Power BI files (models and dashboards)  
- `docs/` – proposal and future documentation (TECHNICAL, METHODOLOGY)  
- `.gitignore` – excludes data files, temp files, and secrets (e.g., `.env`)[file:107][file:145]

## Getting Started (early plan)
1. Acquire small samples of calls-for-service and parking datasets from the Syracuse Open Data Portal.  
2. Run initial EDA in Python/SQL to profile structure, date coverage, and missing values.  
3. Define the first version of the Power BI model and import cleaned tables.  
4. Incrementally build and refine the dashboard pages as analysis progresses.[file:107][file:145]
