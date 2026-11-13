# E-commerce SQL Data Warehouse and Customer Analytics

An end-to-end data project: a SQL Server data warehouse built from raw CRM and ERP files, followed by a customer analysis and an executive Power BI dashboard.

## The project at a glance

- **Part 01: SQL Data Warehousing.** Loads six CSV files into SQL Server and moves them through Bronze (raw), Silver (cleaned) and Gold (business-ready) layers, with validation checks and full documentation.
- **Part 02: SQL Data Analysis.** Builds a customer report view on the Gold layer, then a Power BI dashboard and a written report with insights and recommendations.

## What the analysis found

- Revenue of **$29.35M** from **18,482 customers**.
- **9% of customers (VIPs) bring 37% of revenue.**
- Customers with exactly two orders bring **54% of revenue**, so the biggest opportunity is turning one-order customers into repeat buyers.
- **46%** of customers have not ordered in six months or more, which points to a win-back opportunity.

## Where to look

- Start with [Part 01](Part_01_sql_data_warehousing_project/README.md) to see how the warehouse is built.
- Then read [Part 02](Part_02_sql_data_analysis_project/README.md) for the analysis, dashboard and findings.

## Tools

SQL Server, SQL Server Management Studio (SSMS), Power BI, DAX.

## Repository structure

```
ecommerce-sql-data-warehouse-and-analysis/
|-- Part_01_sql_data_warehousing_project/
|   |-- datasets/      6 CSV files (CRM and ERP sources)
|   |-- docs/          5 PNG diagrams, 2 Markdown files
|   |-- script/        6 SQL files (initialization, bronze, silver, gold)
|   |-- data_validation/   2 SQL files
|   `-- README.md
|-- Part_02_sql_data_analysis_project/
|   |-- docs/          dashboard (PBIX, PDF) and storytelling (PDF report)
|   |-- script/        report_customers.sql
|   `-- README.md
|-- README.md          (summary shown on the GitHub front page)
`-- README.pdf         (printable summary)
```

## About Me

**Adah Martins Oyikwu**

Data analyst focused on SQL Server and Power BI.

- Email: [adahmatins01@gmail.com](mailto:adahmatins01@gmail.com)
- LinkedIn: [www.linkedin.com/in/adah-oyikwu-561b1644a](https://www.linkedin.com/in/adah-oyikwu-561b1644a)
