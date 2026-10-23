# Excel Data Analytics Portfolio

Four end-to-end Excel analytics projects covering data preparation, data-quality validation, PivotTables, the Excel Data Model, and interactive dashboards.

**Author:** Rojan Chandra Poudel

Each project starts from raw data, documents its quality checks, and ends in a dashboard that answers a specific business question. Where the source data is public, the original files are included so the analysis can be reproduced.

---

## Projects at a glance

| # | Project | Domain | Records | Headline result | Tools |
|---|---------|--------|---------|-----------------|-------|
| 1 | [Sales Performance Dashboard](PROJECT_1/) | US retail 2018–2021 | 8,888 order lines | 15.70% margin on $5.33M sales; discounting is the main loss driver | Excel Tables, PivotTables, PivotCharts, slicers |
| 2 | [Global E-Commerce Dashboard](PROJECT_2/) | Global e-commerce 2023–2025 | 2,000 orders | 32.79% margin; margin falls as discount band rises | Excel Tables, validation formulas, PivotTables, slicers |
| 3 | [AdventureWorks Time Series Dashboard](PROJECT_3/) | AdventureWorks reseller | 60,399 sales rows | Year-over-year revenue, COGS and margin with one-click slicers | Data Model (Power Pivot), DAX-style measures, macros |
| 4 | [Olist E-Commerce Analysis](Olist%20E-Commerce%20Project/) | Brazilian marketplace 2016–2018 | 99,441 orders | 91.9% on-time delivery, 4.09/5 average review, 3.0% repeat customers | Power Query, Data Model, join checks, PivotTables |

---

## What each project demonstrates

### 1. Sales Performance Dashboard (`PROJECT_1/`)

A four-year retail sales workbook built to answer three questions: what drives profit, which products lose money, and how the trend moved.

**Headline figures**

| Measure | Value |
|---------|-------|
| Total sales | $5,326,816.11 |
| Total profit | $836,572.94 |
| Profit margin | 15.70% |
| Orders | 4,208 |

**Key findings**

- **West and Technology drive profit.** West earns 40.5% of total profit from 32.3% of sales (19.7% margin). Technology earns 75.9% of profit from 50.1% of sales (23.8% margin).
- **Central is the weak spot.** It generates 23.7% of sales but only 10.4% of profit.
- **Discount is the cause of the losses.** Lines discounted above 40% lost $292.8K. Tables lose $84.1K overall, yet are profitable at 0% discount.
- **Growth was strong but 2020 broke the pattern.** Sales grew 46.9% and profit 70.5% across 2018–2021, but in 2020 sales rose 12.4% while profit fell 10.3%.

### 2. Global E-Commerce Dashboard (`PROJECT_2/`)

Two thousand e-commerce orders turned into a slicer-driven dashboard, with every source field validated before any analysis ran.

**Headline figures**

| Measure | Value |
|---------|-------|
| Total sales | $484,559.34 |
| Total profit | $158,872.32 |
| Overall profit margin | 32.79% |
| Orders | 2,000 |

**Data-quality checks passed**

- No blanks in any of the 15 source fields
- No repeated `Order_ID` values and no fully duplicated rows
- All 2,000 dates recognised as real dates; all numeric fields fully numeric
- `Total_Sales` reconciles to `Quantity × Unit_Price × (1 − Discount ÷ 100)` within one cent on every row

This folder also contains **Jaldimai Foods Sales Manager**, a 12-tab sales-entry and reporting workbook for a two-branch food business in Damak and Birtamode (NPR), with master data for branches, restaurants and menus, plus a demo dataset spanning 2023–2026.

### 3. AdventureWorks Time Series Dashboard (`PROJECT_3/`)

A macro-enabled workbook that puts a star-schema Data Model behind a single time-series dashboard.

- **Fact table:** `FactInternetSales` — 60,399 rows
- **Dimensions:** `DimProduct` (607), `DimCustomer` (18,485), `DimDate` (2,192), `DimGeography` (656), `DimSalesTerritory` (12)
- **Measures:** Total Revenue, COGS, Total Profit, % Profit Margin, Total QTY, Transactions, YoY Change
- **Filters:** country, month name and year slicers; one-click year selection drives current-year vs previous-year comparison

> The dashboard lives in a `.xlsm` file because it uses macros. If Windows blocks it after download, right-click the file → **Properties** → tick **Unblock**.

### 4. Olist E-Commerce Analysis (`Olist E-Commerce Project/`)

The largest project: nine related Kaggle CSVs modelled in Power Query and the Excel Data Model, with explicit join checks so a one-to-many relationship never inflates a total.

**Verified measures**

| Measure | Result | Scope |
|---------|--------|-------|
| Orders | 99,441 | All recorded statuses |
| Delivered item price | 13,221,498.11 | Delivered item rows, freight excluded |
| On-time delivery | 91.9% | 88,644 of 96,470 eligible orders |
| Average review | 4.09 / 5 | 99,224 review records |
| Repeat-customer share | 3.0% | 2,801 of 93,358 delivered customers |

Includes a written documentation report and a 13-slide presentation. The analysis workbook itself is excluded from this repository because it exceeds GitHub's file-size limit — see that folder's README for the rebuild steps.

---

## Repository layout

```
.
├── README.md                  <- you are here
├── notes.txt                  <- data-profiling notes for the Olist datasets
├── PROJECT_1/                 <- Sales Performance Dashboard 2018–2021
│   ├── README.md
│   ├── Sales_Dashboard_Project.xlsx
│   └── Sales_Data_2018_2021.xlsx
├── PROJECT_2/                 <- Global E-Commerce Dashboard + Jaldimai Foods
│   ├── README.md
│   ├── Jaldimai_Foods_Sales_Manager.xlsx
│   ├── global_ecommerce_sales.csv
│   ├── global_Dashboard_Analysis.csv
│   └── Global_Ecommerce_Sales_Dashboard_Project_Notes.docx
├── PROJECT_3/                 <- AdventureWorks Time Series Dashboard
│   ├── README.md
│   ├── EXCEL WORK/Dashboard.xlsm
│   ├── Databases/AdventureWorks.xlsx
│   └── Images/
└── Olist E-Commerce Project/   <- Brazilian marketplace analysis
    ├── README.md
    ├── project details/
    └── olist_*.csv
```

---

## Data sources

| Dataset | Source | Licence note |
|---------|--------|--------------|
| Olist Brazilian E-Commerce | [Kaggle](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce) | Public dataset, 2016–2018 historical records |
| Global E-Commerce Sales | [Kaggle](https://www.kaggle.com/datasets/muhammadaammartufail/global-e-commerce-sales-and-customer-data) | Public dataset, 2023–2025 |
| AdventureWorks | Microsoft sample database | Sample data |
| Sales 2018–2021 | Sample / synthetic | Illustrative only |

Findings describe the recorded data in each dataset and are not statements about current market conditions.

---

## Opening the workbooks

1. Clone the repository.
2. Open the `.xlsx` / `.xlsm` files in desktop Excel (Microsoft 365 recommended).
3. Enable editing if Excel opens in Protected View — Power Query refreshes, slicers and macros need it.
4. To refresh a dashboard, use **Data → Refresh All**.
