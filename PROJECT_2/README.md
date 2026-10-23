# Project 2 — Global E-Commerce Sales Dashboard 2023–2025

Two thousand e-commerce orders turned into an interactive dashboard, with every source field validated before any analysis ran.

| | |
|---|---|
| **Data** | 2,000 orders × 15 fields, January 2023 – December 2025 |
| **Source** | [Kaggle — Global E-Commerce Sales & Customer Data](https://www.kaggle.com/datasets/muhammadaammartufail/global-e-commerce-sales-and-customer-data) |
| **Tools** | Excel Tables, validation formulas, PivotTables, slicers, KPI cards |

---

## Headline figures

| Measure | Value |
|---------|-------|
| Total sales | $484,559.34 |
| Total profit | $158,872.32 |
| Overall profit margin | 32.79% |
| Orders | 2,000 |

**Project question:** Where are sales and profit coming from, and which parts of the business should be investigated more closely?

---

## Files

| File | Purpose |
|------|---------|
| `global_ecommerce_sales.csv` | Raw source data — 2,000 rows, 15 fields |
| `global_Dashboard_Analysis.csv` | Exported analysis output |
| `Global_Ecommerce_Sales_Dashboard_Project_Notes.docx` | Full written report: method, formulas and findings |
| `Jaldimai_Foods_Sales_Manager.xlsx` | Separate workbook — sales management system (see below) |

---

## Workbook structure

| Sheet | Role |
|-------|------|
| `Raw_Data` | Reference copy of the imported source |
| `Clean_Data` | Working table `tblCleanSales`, used for calculated fields and PivotTables |
| `Data_Quality` | Blank, duplicate, type, range and arithmetic checks |
| `Analysis` | PivotTables for regional, product, discount, time and segment comparisons |
| `Dashboard` | KPI summary, charts, slicers, and a filtered table of products with negative profit |
| `Findings` | Evidence-based takeaways and follow-up questions |

---

## Data-quality checks

All checks were run before any value was changed, on the untouched `tblSales` table.

| Check | Formula | Result |
|-------|---------|--------|
| Blanks per field | `=COUNTBLANK(tblSales[Order_ID])` repeated per field | 0 in all 15 fields |
| Repeated order IDs | `=SUMPRODUCT(--(COUNTIF(tblSales[Order_ID],tblSales[Order_ID])>1))` | 0 |
| Exact duplicate rows | 15-field `COUNTIFS` comparison | 0 |
| Row count | `=ROWS(tblSales[Order_ID])` | 2,000 |
| Real dates | `=COUNT(tblSales[Order_Date])` | 2,000 |
| Numeric fields | `=COUNT(...)` on Quantity, Unit_Price, Discount_Percent, Total_Sales, Shipping_Cost, Profit | 2,000 each |
| Quantity range | `MIN` / `MAX` | 1 – 15 |
| Discount range | `MIN` / `MAX` | 0 – 30, in 5-point steps |
| Sales arithmetic | `=SUMPRODUCT(--(ABS(tblSales[Total_Sales]-(tblSales[Quantity]*tblSales[Unit_Price]*(1-tblSales[Discount_Percent]/100)))>0.01))` | 0 mismatches |

The sales-arithmetic check matters most: a mismatched amount would distort every downstream total and chart.

**Formatting decisions.** `Order_Date` as short date; `Quantity` as whole number; price, sales, shipping and profit as currency; `Discount_Percent` with the custom format `0"%"` so a stored value of `5` displays as `5%` without becoming `500%`.

---

## Findings

- **North America** had the strongest regional margin.
- **Clothing & Accessories** had the strongest category margin.
- **Margins fell as the discount band rose** — the higher the discount, the thinner the profit.
- Sales and profit do not tell the same story on their own: a region or category can look strong on revenue while contributing disproportionately little profit.

---

## Jaldimai Foods Sales Manager

A second, unrelated workbook in this folder: a 12-tab sales-entry and reporting system for a two-branch food business in **Damak** and **Birtamode**, Nepal. All amounts are in **NPR**.

| Tab | Role |
|-----|------|
| `Home` | Landing page with quick-action cards and a live snapshot |
| `Dashboard` | Branch and year filters, KPI cards, branch comparison, monthly trend, four-year comparison, top items |
| `Sales Entry` | Order capture form — branch, restaurant, food, optional drinks |
| `Sales_Data` | Transaction log |
| `Order_Summary` | Per-order rollup |
| `Reports` | Reporting views |
| `Branch_Master`, `Restaurant_Master`, `Menu_Master`, `Historical_Price_Master` | Master data |
| `Sources`, `Lists` | Lookup and validation lists |

**Demo snapshot (all branches, 2026):** sales 173,060 · orders 199 · items sold 838 · average order 869.65. Birtamode leads with 103,500 against Damak's 69,560.

> **Note on the save button.** The workbook ships with simulated demo data for 2023–2026. The one-click **SAVE SALE** button is a macro: to activate it, save the workbook as `.xlsm`, import `SaveSale.bas`, and run `InstallSaveButton` once.

---

## Reproducing it

1. Open `Jaldimai_Foods_Sales_Manager.xlsx` or the dashboard workbook in desktop Excel.
2. Enable editing if it opens in Protected View.
3. Use the slicers to filter; PivotTables refresh from `Clean_Data` / `tblCleanSales`.
