# Part 01: SQL Data Warehousing Project

Builds a SQL Server data warehouse for e-commerce data. Customer, product and sales data from two source systems (CRM and ERP) are loaded from CSV files and moved through three layers: **Bronze**, **Silver** and **Gold**.

## Objective

- Bring data from two source systems into one place.
- Clean and standardise it so it can be trusted.
- Provide a business-ready model that analysts can query and report on. Part 02 of this project reads from it.

## Data sources

| System | File | Content |
|---|---|---|
| CRM | `cust_info.csv` | Customer information |
| CRM | `prd_info.csv` | Product information |
| CRM | `sales_details.csv` | Sales transactions |
| ERP | `cust_az12.csv` | Additional customer details |
| ERP | `loc_a101.csv` | Customer locations |
| ERP | `px_cat_g1v2.csv` | Product categories |

## Architecture

| Layer | Purpose | Scripts |
|---|---|---|
| **Initialization** | Sets up the database and schemas the layers live in. | `init_database.sql` |
| **Bronze** | Raw data, loaded as it arrives from the CSV files with `BULK INSERT`. No changes are made to the data. | `ddl_bronze.sql`, `bulk_insert_bronze.sql` |
| **Silver** | Cleaned and standardised data. A stored procedure transforms the Bronze tables and loads them. | `ddl_silver.sql`, `proc_load_silver.sql` |
| **Gold** | Business-ready model for reporting, built as views such as `gold.dim_customers` and `gold.fact_sales`. | `ddl_gold.sql` |
| **Validation** | Checks on the Silver and Gold layers to confirm the data is consistent. | `validation_silver.sql`, `validation_gold.sql` |

The diagrams in `docs/` show the architecture (`data_architecture.png`, `layered_data_architecture.png`), how data moves between layers (`data_flow.png`), how the sources connect (`data_integration.png`) and the final model (`data_model.png`).

## How to run

1. Run `script/initialization/init_database.sql`.
2. Run `script/bronze_layer/ddl_bronze.sql` to create the Bronze tables.
3. Edit the file paths in `script/bronze_layer/bulk_insert_bronze.sql` so they point to the CSV files on your machine, then run it.
4. Run `script/silver_layer/ddl_silver.sql`, then `proc_load_silver.sql`, then execute the stored procedure it creates.
5. Run `script/gold_layer/ddl_gold.sql` to create the Gold views.
6. Run the scripts in `data_validation/` to check the Silver and Gold layers.

## Documentation

- `docs/data_catalog.md`: describes the tables and columns in the Gold layer.
- `docs/naming_convention.md`: the naming rules used for schemas, tables and columns.

## Repository structure

```
Part_01_sql_data_warehousing_project/
|-- datasets/
|   `-- sources/
|       |-- crm/
|       |   |-- cust_info.csv
|       |   |-- prd_info.csv
|       |   `-- sales_details.csv
|       `-- erp/
|           |-- cust_az12.csv
|           |-- loc_a101.csv
|           `-- px_cat_g1v2.csv
|-- docs/
|   |-- data_architecture.png
|   |-- data_flow.png
|   |-- data_integration.png
|   |-- data_model.png
|   |-- layered_data_architecture.png
|   |-- data_catalog.md
|   `-- naming_convention.md
|-- script/
|   |-- initialization/
|   |   `-- init_database.sql
|   |-- bronze_layer/
|   |   |-- ddl_bronze.sql
|   |   `-- bulk_insert_bronze.sql
|   |-- silver_layer/
|   |   |-- ddl_silver.sql
|   |   `-- proc_load_silver.sql
|   `-- gold_layer/
|       `-- ddl_gold.sql
|-- data_validation/
|   |-- silver_layer/
|   |   `-- validation_silver.sql
|   `-- gold_layer/
|       `-- validation_gold.sql
`-- README.md
```

## Tools

SQL Server and SQL Server Management Studio (SSMS).

## Next step

The Gold layer is used for analysis in [Part 02](../Part_02_sql_data_analysis_project/README.md).
