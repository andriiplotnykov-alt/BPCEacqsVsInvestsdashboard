# BPCE Acquisitions & Investments Dashboard

## 📌 Project Overview

This project presents an interactive **Power BI dashboard** designed to analyze the **acquisitions and investment activity of the BPCE Group** across time, sectors, and geographies. 

The objective of the project is twofold: first, to demonstrate the ability to **source, structure, and standardize real-world financial data**;
 second, to showcase the construction of a **decision-oriented BI solution** using Power BI and DAX.

---

## 🎯 Key Features

* **Dynamic slicers** to switch between *Acquisitions* and *Investments*, filter by *year* and *sector*
* **KPI card** displaying total deal value based on active filters
* **Geographical map** visualizing deal size and deal type across countries
* **Time-series chart** showing the number of deals by year
* **Horizontal bar chart** breaking down deal count by sector and deal type
* **Detailed transaction table** including company name, sector, deal date, country, and median deal value

![AAVE Transaction Dashboard](<BPCEacqVsinvstmnts/docs/Dashboard_screenshotBPCE.png>)

---

## Data & Methodology

### Data Collection

* Open-source acquisition and investment data collected via **web scraping** of publicly available articles
* Supplementary deal intelligence sourced from **Tracxn**
* Raw data consolidated in **Excel**, resulting in two core datasets:

  * Acquisitions table
  * Investments table

### Data Preparation

* Standardization of sector names, countries, deal values, and dates
* Harmonization of acquisition and investment schemas
* Appending datasets into a unified fact table for analysis

### Modeling & Analytics

* Creation of calculated measures in **DAX** to support KPIs and advanced aggregations
* Example: formatted average deal size measure adapting dynamically to slicer context

---

## 📊 Example DAX Measure

```DAX
AverageDealSizeFormatted =
VAR AvgDeal =
    CALCULATE(
        DIVIDE([TotalDealValue], [TotalDealsCount]),
        ALLSELECTED(Append1)
    )
RETURN
SWITCH(
    TRUE(),
    AvgDeal >= 1000000000, FORMAT(CEILING(AvgDeal/1000000000,0.01), "#,0.##") & " Bn",
    AvgDeal >= 1000000, FORMAT(CEILING(AvgDeal/1000000,0.01), "#,0.##") & " M",
    FORMAT(CEILING(AvgDeal,1), "#,0")
)
```

---

## 🗂 Repository Structure

```
BPCE-Acquisitions-Investments-Dashboard/
│
├── data/
│   ├── raw/                  # Raw scraped and sourced datasets
│   ├── processed/            # Cleaned and standardized Excel files
│
├── powerbi/
│   ├── BPCE_Dashboard.pbix   # Power BI dashboard file
│
├── docs/
│   ├── dashboard_screenshots/
│   
│
└── README.md
```

---

## 🚀 What This Project Demonstrates

* End-to-end **data pipeline thinking**, from raw information gathering to analytical output
* Practical experience in **Power BI data modeling**, relationship design, and performance-aware DAX
* Ability to translate financial transaction data into **clear business narratives**
 

 

