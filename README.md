# Retail Sales Analytics | Power BI

**End-to-End Business Intelligence & Data Analytics Portfolio Project**

An interactive retail sales analytics solution developed using **Microsoft Power BI Desktop, Power Query, and DAX** to monitor business performance, identify sales trends, analyze customer behavior, and support data-driven decision-making.

The project covers the complete Business Intelligence workflow, from raw data preparation and dimensional modeling to interactive reporting, advanced DAX calculations, and Row-Level Security (RLS).

**Project Scope:** 2024–2025 | 3,000 Orders | 350 Customers | 18 Products | 4 Stores

---

## Business Objectives

The main objectives of this project are to:

- Monitor key business performance indicators, including revenue, orders, units sold, and average order value.
- Analyze sales trends across different periods and compare year-over-year performance.
- Identify top-performing products, customers, and product categories.
- Evaluate revenue distribution across customer segments and store regions.
- Enable interactive exploration through dynamic filters, rankings, drill-through, and bookmarks.
- Simulate enterprise-level data access using Dynamic Row-Level Security.

## Key Performance Indicators

| KPI | Value |
|---|---:|
| Total Revenue | €639,766.28 |
| Total Orders | 3,000 |
| Units Sold | 5,248 |
| Active Customers | 350 |
| Total Products | 18 |
| Average Order Value | €213.26 |
| Revenue per Customer | €1,827.90 |
| Revenue 2024 | €316,700.54 |
| Revenue 2025 | €323,065.74 |
| Revenue Growth (2025 vs. 2024) | +2.01% |

---

## Dashboards

### 1. Sales Overview

An executive-level dashboard providing a comprehensive view of overall sales performance.

**Key Features:**
- Revenue, orders, units sold, and average order value KPIs.
- Monthly revenue trends.
- Revenue distribution by product category.
- Annual revenue comparison.
- Interactive filters for year, store region, and category.

![Sales Overview](screenshots/01-sales-overview.png)

### 2. Sales Performance

A dashboard focused on analyzing sales evolution and comparing performance across different periods.

**Key Features:**
- Year-to-Date (YTD) revenue.
- Previous Year (PY) revenue.
- Year-over-Year (YoY) revenue growth.
- Monthly sales comparison between 2024 and 2025.
- Interactive year selection.
- Time Intelligence calculations using DAX.

![Sales Performance](screenshots/02-sales-performance.png)

### 3. Products & Customers

An interactive dashboard designed to identify the products and customers that contribute most to business revenue.

**Key Features:**
- Dynamic Top 3, Top 5, and Top 10 product rankings.
- Product analysis by revenue and units sold.
- Customer revenue rankings using RANKX.
- Revenue by customer segment.
- Revenue per customer KPI.
- Interactive filters for year, category, and store region.

![Products & Customers](screenshots/03-products-customers.png)

### 4. Product Details — Drill-through

A detailed product-level analysis page accessible through drill-through interactions.

**Key Features:**
- Product-specific revenue, orders, and units sold.
- Monthly product revenue trends.
- Customer-level sales contributions.
- Context-sensitive filtering.
- Navigation back to the main report.

![Product Details](screenshots/04-product-details.png)

---

## Business Insights

The analysis identified several business patterns and performance indicators.

### Revenue Growth

Total revenue increased from **€316,700.54 in 2024** to **€323,065.74 in 2025**, representing approximately **2.01% year-over-year growth**.

This indicates modest overall sales growth during the analyzed period.

### Product Category Performance

| Category | Total Revenue | Revenue Share |
|---|---:|---:|
| Home | €233,201.55 | 36.45% |
| Electronics | €212,208.40 | 33.17% |
| Sports | €194,356.31 | 30.38% |

The **Home** category generated the highest revenue, contributing approximately 36.45% of total sales.

Revenue was relatively balanced across the three product categories.

### Top-Performing Products

The highest-revenue products included:

1. Coffee Maker — €72,021.18
2. Headphones — €70,559.26
3. Yoga Mat — €66,336.82
4. Vacuum — €65,497.24
5. Desk Lamp — €58,988.90

These products represent key contributors to the company's sales performance.

### Customer Segmentation

The **Consumer** segment generated the highest revenue, approximately **€225,522**, followed by Small Business and Corporate customers.

Customer segmentation provides opportunities to investigate purchasing behavior and identify high-value customer groups.

### Business Recommendations

Based on the analysis, the following areas could be explored further:

- Investigate the factors driving revenue growth between 2024 and 2025.
- Monitor the performance of top-selling products and categories.
- Analyze purchasing frequency and revenue contribution among high-value customers.
- Explore regional differences in sales performance.
- Incorporate product cost and margin metrics to assess profitability rather than revenue alone.

*These recommendations are exploratory and would require additional business context before implementation.*

---

## Data Model

The solution follows a **Star Schema**, separating transactional data from descriptive dimensions.

### Fact Table

**FactSales**
- OrderID
- OrderDate
- CustomerID
- ProductID
- StoreID
- Quantity
- UnitPrice
- DiscountPct
- Revenue

### Dimension Tables

**DimProducts:** Product information, categories, and costs.

**DimCustomers:** Customer attributes, cities, regions, and segments.

**DimStores:** Store locations and geographical regions.

**DimDate:** Calendar dimension supporting time-based analysis.

### Supporting Tables

**_Measures:** Centralized DAX measures.

**TopN Selection:** Disconnected table supporting dynamic Top N filtering.

**UserAccess:** Fictional user-access configuration supporting Dynamic RLS.

The relationships between the main dimension tables and FactSales use one-to-many cardinality and single-direction filtering.

![Data Model](screenshots/05-data-model.png)

---

## Technical Implementation

### Data Preparation — Power Query

The ETL process includes:

- CSV data ingestion.
- Data type validation and conversion.
- Handling missing values.
- Removing duplicate records.
- Standardizing categorical attributes.
- Creating calculated revenue.
- Preparing clean tables for dimensional modeling.

### DAX & Analytical Measures

The project uses DAX functions including:

`SUM`, `SUMX`, `COUNTROWS`, `DISTINCTCOUNT`, `DIVIDE`, `CALCULATE`, `FILTER`, `ALL`, `ALLSELECTED`, `RANKX`, `TOTALYTD`, `SAMEPERIODLASTYEAR`, and `SELECTEDVALUE`.

Examples of implemented metrics include:

- Total Revenue
- Total Orders
- Average Order Value
- Revenue YTD
- Revenue Previous Year
- Revenue YoY %
- Revenue by Category
- Product Revenue Rank
- Customer Revenue Rank
- Revenue per Customer

### Interactive Reporting

The report includes:

- Interactive slicers.
- Dynamic Top N selections.
- Revenue and units comparison.
- Drill-through analysis.
- Report page tooltips.
- Bookmarks.
- Page navigation.

---

## Row-Level Security (RLS)

The project implements both Static and Dynamic Row-Level Security to simulate enterprise data-access requirements.

### Static RLS

Static roles restrict access to specific stores or regions using DAX filters.

### Dynamic RLS

Dynamic RLS uses a fictional user-access table and `USERPRINCIPALNAME()` to determine authorized data based on the simulated user's identity.

The access model supports:

| User Role | Access Level |
|---|---|
| Sales Director | All sales data |
| Regional Manager | Assigned region only |
| Store Manager | Assigned store only |
| Unauthorized User | No sales access |

RLS scenarios were tested locally using **Modeling → View as** in Power BI Desktop.

**Note:** User assignment and deployment to Power BI Service were not performed. All user identities used for testing are fictional.

---

## Data Quality & Validation

Data validation includes:

- Duplicate record detection and removal.
- Data type checks.
- Missing-value handling.
- Revenue reconciliation between Power Query and DAX calculations.
- Verification of transactional and aggregated KPIs.
- Testing of interactive filters and rankings.
- Validation of Static and Dynamic RLS scenarios.

The original cleaned dataset contains **3,000 unique orders**.

---

## Tools & Technologies

- Microsoft Power BI Desktop
- Power Query (M)
- DAX
- Dimensional Modeling
- Data Visualization
- CSV
- GitHub

---

## Project Structure

```text
powerbi-sales-analytics/
|
|-- data/
|   |-- raw/
|       |-- Sales.csv
|       |-- Products.csv
|       |-- Customers.csv
|       |-- Stores.csv
|       |-- Returns.csv
|       |-- Targets.csv
|
|-- powerbi/
|   |-- Sales_Analytics.pbix
|
|-- screenshots/
|   |-- 01-sales-overview.png
|   |-- 02-sales-performance.png
|   |-- 03-products-customers.png
|   |-- 04-product-details.png
|   |-- 05-data-model.png
|
|-- README.md
```

## How to Run

1. Clone or download this repository.
2. Install Microsoft Power BI Desktop if necessary.
3. Open `powerbi/Sales_Analytics.pbix`.
4. If the original CSV paths are unavailable, open **Transform Data → Data Source Settings** or update the file paths in Power Query.
5. Point the data sources to the corresponding files in `data/raw/`.
6. Select **Close & Apply**.
7. Select **Refresh** to reload the data.
8. Explore the dashboards, slicers, rankings, and drill-through functionality.

### Requirements

- Microsoft Power BI Desktop
- Windows operating system
- Access to the included CSV files

A Power BI Service account is not required to explore the project locally.

---

## Limitations & Future Improvements

Potential future developments include:

- Deployment to Power BI Service.
- Automated scheduled data refresh.
- Integration with SQL databases or cloud data sources.
- Profitability analysis using product costs and margins.
- Additional customer retention and purchase-frequency metrics.
- Further optimization and performance benchmarking.

---

## Project Notes

This project uses **fictional retail data** for educational and portfolio purposes.

The business insights and recommendations are based on simulated transactions and do not represent a real company's financial performance.

The Power BI report was developed and tested locally using Power BI Desktop.

---

## Author

**Miguel Ferreira**

Business Intelligence & Data Analytics

[GitHub Profile](https://github.com/miguelhbpferreira-dev)

