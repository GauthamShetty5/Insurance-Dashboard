# 🚗 Insurance Analytics Dashboard — Power BI

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![Snowflake](https://img.shields.io/badge/Snowflake-29B5E8?style=for-the-badge&logo=snowflake&logoColor=white)
![DAX](https://img.shields.io/badge/DAX-217346?style=for-the-badge&logo=microsoftexcel&logoColor=white)
![Status](https://img.shields.io/badge/Status-Active-success?style=for-the-badge)

An end-to-end vehicle insurance analytics dashboard built in Power BI Desktop, covering policy issuance, premium collection, claims behavior, and loss ratio performance across a 2014–2018 book of business.

---

## 📊 Dashboard Preview

The report gives a single-page 360° view of the insurance book: who is buying policies, how claims flow over time, and where the premium-to-claim relationship turns unprofitable.

**Key KPI strip:** Policies Opened · Total Premium · Total Claims · Avg Premium · Avg Claim · Claim Count · Premium to Claim Ratio

---

## 🗂️ Data Source & Pipeline

| Stage | Tool | Description |
|---|---|---|
| 1️⃣ Extraction | ❄️ **Snowflake** | Raw policy and claims data extracted from our Snowflake data warehouse |
| 2️⃣ Cleaning & Shaping | 🔧 **Power Query (M)** | Data type corrections, date parsing, null handling, and column pruning performed before load |
| 3️⃣ Modeling | 📥 **Power BI Desktop** | Cleaned tables imported into Power BI's data model |
| 4️⃣ Calculation Layer | 🧮 **DAX** | Custom measures built for all KPIs, ratios, and conditional visuals |

### Core Dataset Fields
`SEX` · `INSR_BEGIN` / `INSR_END` · `EFFECTIVE_YR` · `INSR_TYPE` · `INSURED_VALUE` · `PREMIUM` · `OBJECT_ID` · `PROD_YEAR` · `SEATS_NUM` · `CARRYING_CAPACITY` · `TYPE_VEHICLE` · `CCM_TON` · `MAKE` · `USAGE` · `CLAIM_PAID`

A supporting **Calendar** table (date dimension) is used for time intelligence — Day, Month, Month Num, Quarter, QY, Year.

---

## 🧮 DAX Measures

Custom measures power every KPI card and conditional visual, including:

- `Policies Opened`, `Policies Closed`, `Policy Count`
- `Total Premium`, `Total Claims`, `Avg Premium`, `Avg Claim`, `Avg Claim2`
- `Claim Count`
- `Premium to Claim Ratio` — the headline profitability metric, calculated as Total Claims ÷ Total Premium

---

## 📈 Visuals & Features Used

| Visual / Feature | What it shows |
|---|---|
| 🚙 **Conditional-formatted icons** | Icons next to each vehicle type (Motor-cycle, Truck, Pick-up, etc.) change dynamically based on selection/context — driven by conditional formatting rules on the "Who is buying our policies?" bar chart |
| 🎗️ **Ribbon chart ("Claim Flow")** | Shows how claim volume shifts in rank/share across usage categories (Agricultural, Ambulance, Car Hires, etc.) from 2014–2018 |
| 🍩 **Nested donut chart** | A donut placed inside another donut ("Policies Opened vs Claim Count per SEX") — an unconventional layered visual to show two related distributions in one shape |
| 🎯 **Scatter plot with custom tooltip** | "Avg (Premium vs Claims)" scatter plot with a fully custom tooltip page that reveals Policies Opened, Avg Premium, Avg Claim, and Premium to Claim Ratio on hover |
| 🟥🟪 **Split-shaded background regions** | The scatter plot background is visually divided into a loss region (red/pink) and a profit region (purple), making it instantly clear which points sit above or below the breakeven line |
| 🔥 **Heat-matrix table** | "USAGE" matrix with color-scaled conditional formatting (green → yellow → red) showing % change per usage category per year |
| 🎛️ **Slicers / cross-filtering** | Policy Year slicer (2014–2018) drives every visual on the page |
| 🏆 **Top 3 MAKE card** | Ranked mini-visual highlighting the top 3 vehicle manufacturers by policy volume |

---

## 🛠️ Tech Stack

- **Power BI Desktop** — report authoring, data modeling, DAX
- **Power Query (M)** — ETL/data cleaning layer
- **Snowflake** — source data warehouse
- **Git** — version control for `.pbix` / PBIP project files

---

## 🚀 Future Enhancements

- ☁️ **Publish to Power BI Service** for organization-wide access and collaboration
- 🔄 **Scheduled Refresh with Incremental Load** — since new premiums and claims land in Snowflake daily via a batch pipeline, configure incremental refresh policies so only new/changed partitions are reloaded instead of the full dataset
- 🔐 **Row-Level Security (RLS)** — define roles so different teams (e.g., regional managers, claims analysts, executives) only see the slice of data relevant to them, rather than the full dashboard
- 🔖 **Bookmarks** — save curated views/states of the report (e.g., "Claims Focus", "Premium Focus") for guided storytelling and quick navigation
- 📱 **Mobile-optimized layout** for on-the-go access
- 🧭 **Drill-through pages** for deeper per-policy or per-vehicle-type investigation
- 📤 **Alerts on KPI thresholds** (e.g., notify when Premium to Claim Ratio crosses a risk threshold)

---
