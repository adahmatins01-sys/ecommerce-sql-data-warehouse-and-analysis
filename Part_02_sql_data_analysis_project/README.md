# Part 02: SQL Data Analysis Project

Uses the Gold layer from Part 01 to analyse customer behaviour. A SQL view prepares one row per customer, and a Power BI dashboard turns it into an executive report with findings and recommendations.

## Business questions

- Who are our customers, and how valuable are they?
- How loyal are they, and how many orders do they place?
- Which customers have stopped ordering?

## Data

- Source: `gold.fact_sales` and `gold.dim_customers` (built in Part 01).
- Output: the view `gold.report_customers`, with **18,482 customers**.
- Orders run up to **28 January 2014**.

## The SQL view (`script/report_customers.sql`)

The view gathers each customer's name, age and order history, then calculates:

| Field | How it is built |
|---|---|
| Customer segment | **VIP**: active 12 months or more and total sales above $5,000. **Regular**: active 12 months or more and sales of $5,000 or less. **New**: everyone else. |
| Age group | Under 20, 20-29, 30-39, 40-49, 50 and above |
| Recency | Months between the customer's last order and the **latest order date in the data** |
| Average order value | Total sales divided by total orders |
| Average monthly spend | Total sales divided by lifespan in months |

The view measures recency from the latest order date in the data, not from today. Using today's date would give every customer a recency of about 157 months because the data ends in 2014.

## Dashboard (`docs/dashboard/`)

An interactive Power BI report with slicers for segment and age group. It contains:

- KPI cards: revenue, customers, orders, revenue per customer and average order value
- Segment share and segment summary
- Revenue by age group
- Customers and revenue by number of orders
- Customers by last order quarter
- Revenue concentration by customer tenth
- Recency of last order
- Top 8 customers by lifetime sales

The report in `docs/storytelling/` explains each visual with its insight and recommended actions.

## Key findings

- Revenue is **$29.35M** from **18,482 customers** and **27,657 orders**. The average order value is **$1,061**.
- **VIPs are 9% of customers but bring 37% of revenue.**
- Only **37%** of customers have ordered more than once.
- Customers with exactly **two orders bring 54% of revenue**. Their revenue per customer is about five times that of one-order customers.
- The **top 10% of customers bring 40%** of revenue.
- **46%** of customers last ordered six or more months before the data ends, and they hold $13.58M of revenue.

## Recommendations

1. Convert one-order customers into two-order customers with a second-purchase campaign.
2. Protect VIP customers with account management and loyalty benefits.
3. Run a win-back campaign for customers who have not ordered in 6 to 12 months.
4. Track repeat-customer rate and recency every month.

## Limitations

- Age is calculated from today's date, so it is overstated, and no customer appears under 40. Customers with no birth date fall into "50 and above".
- Segments follow fixed rules, so "New" means under 12 months of activity, not necessarily first-time buyers.
- Revenue is sales value only. There is no cost or margin data.
- The last quarter in the data is incomplete.

## Repository structure

```
Part_02_sql_data_analysis_project/
|-- docs/
|   |-- dashboard/
|   |   |-- report_customers.pbix
|   |   `-- report_customers.pdf
|   `-- storytelling/
|       `-- Customer_Executive_Dashboard_Report.pdf
|-- script/
|   `-- report_customers.sql
`-- README.md
```

## Tools

SQL Server, SQL Server Management Studio, Power BI and DAX.
