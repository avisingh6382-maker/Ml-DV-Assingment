# Data Visualization (DV) Assignment

**Author:** Avi Singh

A collection of eight Microsoft Power BI (`.pbix`) experiments covering core data visualization, data preparation, interactive dashboarding, geospatial mapping, part-to-whole analysis, hierarchical heatmaps/treemaps, and time-series forecasting.

## Project Structure

```text
dv/
├── README.md
├── Experiment 1.pbix
├── Experiment 2.pbix
├── Experiment 3.pbix
├── Experiment 4.pbix
├── experiment 5.pbix
├── Experiment 6.pbix
├── Experiment 7.pbix
└── Experiment 8.pbix
```

## Summary of Experiments

| File | Data Model Table | Visuals & Components | Focus / Key Fields |
| :--- | :--- | :--- | :--- |
| `Experiment 1.pbix` | `Superstore_Sales_Experiment1` | Clustered Column Chart, Dual-Axis Line Chart | Sales and Profit by `Category` and `Order Date` hierarchy (`Year` → `Day`) |
| `Experiment 2.pbix` | `PowerBI_Experiment2_Raw_Sales_Data` | Data model only (blank report canvas) | Raw sales data ingestion and Power Query preparation |
| `Experiment 3.pbix` | `PowerBI_Experiment3_Sales_TimeSeries` | Column Chart, Multi-Series Line Chart | Regional `Sales` comparison and `Profit` time-series by `Region` (with `Sales` tooltips) |
| `Experiment 4.pbix` | `PowerBI_Experiment3_Sales_TimeSeries` | 3 Slicers, 2 KPI Cards, Line Chart | Interactive dashboard with `Category`, `Region`, and `Date` slicers; `Sales` and `Profit` KPIs and trend |
| `experiment 5.pbix` | `PowerBI_Experiment5_Geo_Sales_Data` | Bubble Map, Clustered Bar Chart | Geospatial *"Sales Distribution across India"* (`Latitude`/`Longitude`, `Sales`, `Profit`) and `City`-level sales |
| `Experiment 6.pbix` | `PowerBI_Experiment6_Olympic_Medals` | Pie Chart, Donut Chart | Part-to-whole comparison of `Total Medals` by `Country` |
| `Experiment 7.pbix` | `PowerBI_Experiment7_Heatmap_Treemap` | Matrix (Heatmap), Treemap | `Region` × `Category` sales heatmap (conditional gradient fill) and `Category` / `Subcategory` treemap |
| `Experiment 8.pbix` | `PowerBI_Experiment8_TimeSeries_Forecasting` | Line Chart with Trend & Forecast | *"Monthly Sales Trend"* with trend line and 3-period forecast at 95% confidence |

## Experiment Breakdown

### 1. `Experiment 1.pbix` — Superstore Sales & Profit Analysis
Uses `Superstore_Sales_Experiment1` with two visuals on `Page 1`:
- **Clustered Column Chart:** Compares `Sum(Profit)` and `Sum(Sales)` across product `Category`.
- **Line Chart (Dual Y-Axis):** Tracks `Sum(Sales)` (primary axis) and `Sum(Profit)` (secondary axis) across the `Order Date` hierarchy (`Year`, `Quarter`, `Month`, `Day`).

### 2. `Experiment 2.pbix` — Raw Sales Data Preparation
Loads `PowerBI_Experiment2_Raw_Sales_Data` into the Power BI data model. The report page (`Page 1`) contains no visuals, reflecting a data import, inspection, and Power Query preprocessing exercise.

### 3. `Experiment 3.pbix` — Regional Sales & Time-Series Profit
Uses `PowerBI_Experiment3_Sales_TimeSeries` with two visuals on `Page 1`:
- **Column Chart:** Displays `Sum(Sales)` by `Region`.
- **Multi-Series Line Chart:** Plots `Sum(Profit)` over the `Date` hierarchy (`Year`, `Quarter`, `Month`, `Day`) split by `Region` series, with `Sum(Sales)` included in tooltips.

### 4. `Experiment 4.pbix` — Interactive Sales & Profit Dashboard
Builds an interactive report on `PowerBI_Experiment3_Sales_TimeSeries` combining six elements on `Page 1`:
- **Three Slicers:** Filter the dashboard dynamically by `Category`, `Region`, and `Date`.
- **Two KPI Cards:** Display total `Sum(Sales)` and total `Sum(Profit)`.
- **Line Chart:** Visualizes `Sum(Sales)` and `Sum(Profit)` over the `Date` hierarchy (`Year`, `Quarter`, `Month`, `Day`).

### 5. `experiment 5.pbix` — Geospatial Sales Distribution
Uses `PowerBI_Experiment5_Geo_Sales_Data` to analyze geographic sales performance across two visuals on `Page 1`:
- **Map (*"Sales Distribution across India"*):** Plots points by `Latitude` and `Longitude`, sized by `Sum(Sales)` with `Sum(Profit)` tooltips.
- **Clustered Bar Chart:** Ranks `Sum(Sales)` by `City`.

### 6. `Experiment 6.pbix` — Olympic Medals Part-to-Whole Analysis
Uses `PowerBI_Experiment6_Olympic_Medals` to compare medal shares across countries with two visuals on `Page 1`:
- **Pie Chart:** Shows `Sum(Total Medals)` by `Country`.
- **Donut Chart:** Shows `Sum(Total Medals)` by `Country` in ring form for side-by-side comparison.

### 7. `Experiment 7.pbix` — Heatmap & Treemap Hierarchy
Uses `PowerBI_Experiment7_Heatmap_Treemap` with two visuals on `Page 1`:
- **Matrix (Heatmap):** Displays `Sum(Sales)` with `Region` as rows and `Category` as columns, using conditional background color formatting (two-color linear gradient from `#E66C37` minimum to `#118DFF` maximum).
- **Treemap:** Breaks down `Sum(Sales)` hierarchically by `Category` (group) and `Subcategory` (details).

### 8. `Experiment 8.pbix` — Time-Series Trend & Forecasting
Uses `PowerBI_Experiment8_TimeSeries_Forecasting` with a single analytics-enabled visual on `Page 1`:
- **Line Chart (*"Monthly Sales Trend"*):** Plots `Sum(Sales)` across the `Date` hierarchy (`Year`, `Quarter`, `Month`, `Day`), augmented with a **Trend Line** and a **Forecast** configured for a 3-period forecast length at a 95% confidence level.

## Getting Started

### Prerequisites

- **Microsoft Power BI Desktop** (Windows, or via a Windows VM on macOS/Linux)
- These files use the Power BI Desktop report format (`Version 1.32`, created with release `2026.10`); updating to a recent Power BI Desktop release is recommended to avoid compatibility warnings.

### Opening the Reports

1. Download or clone the repository and navigate to the `dv/` folder.
2. Double-click any `.pbix` file (or open it via **File → Open report** inside Power BI Desktop).
3. Interact with slicers, drill-down date hierarchies, tooltips, and analytics panes directly on `Page 1`.

## Author & Credits

- **Author:** Avi Singh (`avisingh6382@gmail.com`)
- **Platform & Tools:** Microsoft Power BI Desktop
- **Datasets:** Embedded experiment tables (`Superstore_Sales_Experiment1`, `PowerBI_Experiment2_Raw_Sales_Data`, `PowerBI_Experiment3_Sales_TimeSeries`, `PowerBI_Experiment5_Geo_Sales_Data`, `PowerBI_Experiment6_Olympic_Medals`, `PowerBI_Experiment7_Heatmap_Treemap`, and `PowerBI_Experiment8_TimeSeries_Forecasting`).
