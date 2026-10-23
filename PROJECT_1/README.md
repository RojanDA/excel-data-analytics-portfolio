# Project 1 — Sales Performance Dashboard 2018–2021

An Excel dashboard built to answer three questions about four years of US retail sales: what drives profit, which products lose money, and how the trend moved year over year.

| | |
|---|---|
| **Data** | 8,888 order lines, January 2018 – December 2021 |
| **Type** | Sample / synthetic dataset, used for illustrative analysis |
| **Tools** | Excel Tables, PivotTables, PivotCharts, slicers, calculated fields |

---

## Headline figures

| Measure | Value |
|---------|-------|
| Total sales | $5,326,816.11 |
| Total profit | $836,572.94 |
| Profit margin | 15.70% |
| Orders | 4,208 |

---

## Files

| File | Purpose |
|------|---------|
| `Sales_Dashboard_Project.xlsx` | The finished analysis: data, pivots, dashboard and written findings |
| `Sales_Data_2018_2021.xlsx` | Raw source extract (8,888 rows × 20 fields) |

### Workbook structure

| Sheet | Role |
|-------|------|
| `Data` | Source table — orders, customers, geography, products, sales, discount, profit |
| `Analysis` | PivotTables backing every dashboard chart |
| `Dashboard` | KPI cards, charts, a Top-10 loss-making products table, and slicers |
| `Findings` | Three answered questions, each with evidence and a recommendation |

**Slicers:** Category · Region · Segment · Year — every one of them filters all charts and KPIs at once.

---

## Data model

Twenty source fields across four dimensions:

- **Order:** `Order ID`, `Order Date`, `Ship Date`, `Ship Mode`
- **Customer:** `Customer ID`, `Customer Name`, `Segment`
- **Geography:** `Country`, `City`, `State`, `Region`
- **Product:** `Product ID`, `Category`, `Sub-Category`, `Product Name`
- **Measures:** `Sales`, `Quantity`, `Discount`, `Profit`

Three product categories (Technology, Furniture, Office Supplies) and three customer segments (Consumer, Corporate, Home Office).

---

## Findings

### Q1 — What drives profit?

West region and the Technology category drive profit. Central is the weak spot.

- West earns **40.5% of total profit from 32.3% of sales** (19.7% margin).
- Technology earns **75.9% of profit from 50.1% of sales** (23.8% margin).
- Central generates **23.7% of sales but only 10.4% of profit**.
- Customer segment makes little difference to margin.

### Q2 — Which products lose money, and is discount the cause?

Yes. Discounting is the main cause of losses.

- Lines discounted **above 40% lost $292.8K** in total.
- **Tables** lost $84.1K (−14.4% margin) and **Bookcases** $2.1K.
- At **0% discount both are profitable** — 10.7% and 15.8% margin respectively.

The Top-10 loss-making products are dominated by tables and bookcases, all carrying average discounts between 16% and 32%:

| Product | Profit | Sales | Avg discount |
|---------|--------|-------|--------------|
| Lumen Folding Table | −$23,731.03 | $65,322.37 | 27.7% |
| Lumen Conference Table | −$15,918.03 | $87,702.74 | 18.9% |
| Pinnacle Document Scanner | −$11,885.12 | $218,691.02 | 25.0% |
| Lumen Training Table | −$8,017.89 | $62,744.99 | 22.5% |
| Crestwood Folding Table | −$7,920.71 | $30,067.33 | 32.4% |

### Q3 — How did sales and profit trend from 2018 to 2021?

Both grew strongly overall, but 2020 broke the pattern.

- Sales grew **46.9%** ($1.157M → $1.701M) and profit grew **70.5%** ($167.0K → $284.7K).
- In **2020 sales rose 12.4% but profit fell 10.3%**, and margin dropped — the only year where the two measures moved in opposite directions.

---

## Recommendation

Cap discretionary discounts, especially on Tables and Bookcases where a 0% discount is profitable but any meaningful discount turns the line negative. Review the Central region's pricing and discount mix, since it carries a quarter of sales but a tenth of profit.

---

## Reproducing it

1. Open `Sales_Dashboard_Project.xlsx` in desktop Excel.
2. Enable editing if it opens in Protected View.
3. Use the slicers on the `Dashboard` sheet to filter; all charts and KPIs respond.
4. Pivot sources live on the `Analysis` sheet — right-click any PivotTable → **Refresh** after changing `Data`.
