# Superstore Sales & Profitability Dashboard

An interactive Power BI report built with the Sample Superstore dataset. It brings sales performance, regional results, product performance, and profitability into one report, allowing readers to move from a high-level overview to product-level detail.

The project focuses on practical BI work: defining reusable measures, building a date model, organizing analysis into clear report pages, and presenting results in a consistent visual style.

## Report pages

### 1. Sales Overview
A high-level view of total sales, total profit, order count, profit margin, average order value, and the monthly sales trend.

### 2. Regional Analysis
Compares sales across regions, with filters for region and category. It also includes a year-over-year sales growth indicator.

### 3. Product Analysis
Compares sales by category and profit by sub-category. Conditional formatting helps highlight profitable and loss-making sub-categories.

### 4. Profitability Analysis
Focuses on profit margin and compares sales with profit across categories. This helps reveal cases where high sales do not necessarily translate into high profit.

### 5. Product Ranking
Shows product-level sales, profit, profit margin, and quantity, alongside a Top 10 products-by-sales visual.

## Key measures

The report uses DAX measures for its main KPIs and period comparisons. Definitions are available in [`docs/DAX-Measures.md`](docs/DAX-Measures.md).

- **Total Sales** — sum of sales.
- **Total Profit** — sum of profit.
- **Total Orders** — distinct count of order IDs.
- **Profit Margin** — total profit divided by total sales.
- **Average Order Value** — total sales divided by distinct orders.
- **Total Quantity** — sum of quantity.
- **Sales MoM Growth %** — month-over-month sales change.
- **Sales YoY Growth %** — year-over-year sales change.

A dedicated calendar table supports date filtering and time-intelligence calculations.

## Tools and techniques

- Microsoft Power BI Desktop
- DAX measures and a calculated calendar table
- One-to-many date relationship
- Time intelligence with `DATEADD` and `SAMEPERIODLASTYEAR`
- KPI cards, slicers, tables, column charts, and bar charts
- Conditional formatting for profitability analysis
- A dark navy, blue, and teal visual theme

## Dataset

This project uses the **Sample Superstore** dataset for demonstration and portfolio purposes. The report analyzes the sample data; it is not a live company reporting system.

Check the terms and provenance of the specific dataset file you downloaded before redistributing it. This repository should contain the report and documentation. Include the raw dataset only if you have permission to share it.

## Repository structure

```text
PowerBI-Analytics-Portfolio/
├── PowerBI-Analytics-Portfolio.pbix
├── README.md
├── LICENSE
├── .gitignore
├── CONTRIBUTING.md
└── docs/
    ├── Data-Dictionary.md
    ├── DAX-Measures.md
    ├── Model-Overview.md
    └── Screenshots.md
```

## Open the report

1. Install Microsoft Power BI Desktop.
2. Clone or download this repository.
3. Open `PowerBI-Analytics-Portfolio.pbix`.
4. If Power BI requests a data-source path, point it to your local Sample Superstore file and confirm that the table and column names match the model.
5. Refresh the report if needed, then explore the five pages.

The exact refresh steps depend on how the dataset was imported and where the local file is stored.

## Notes on interpretation

- Profit margin is calculated from aggregated profit and sales, not by averaging row-level margins.
- Total orders counts distinct `Order ID` values; it is not a count of order lines.
- Month-over-month and year-over-year measures depend on the calendar table and the available date range. A prior-period value may be blank when no comparable period exists.
- The report reflects the sample dataset and should not be treated as validated financial reporting.

## Project status



## Dashboard Previews

### 1. Sales Overview
![Sales Overview](screenshots/sales-overview.png)

### 2. Regional Analysis
![Regional Analysis](screenshots/regional-analysis.png)

### 3. Product Analysis
![Product Analysis](screenshots/product-analysis.png)

### 4. Profitability Analysis
![Profitability Analysis](screenshots/profitability-analysis.png)

### 5. Product Ranking
![Product Ranking](screenshots/product-ranking.png)


The five report pages and their main visuals have been built and formatted. Add screenshots of the final report to the `screenshots/` directory and update the image section when they are ready.

## Author

Created as a Power BI portfolio project demonstrating data modeling, DAX, time-based analysis, and dashboard design.
