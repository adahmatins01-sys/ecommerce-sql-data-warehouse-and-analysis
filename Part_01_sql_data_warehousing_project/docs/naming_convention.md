# Naming Conventions

## General Principles
- Use `snake_case` with lowercase letters.
- Language: English only.
- Avoid SQL reserved words.

---

## Table Naming Conventions

### Bronze & Silver Rules
- `<sourcesystem>_<entity>`
- Example: `crm_customer_info`

### Gold Rules
- `<category>_<entity>`
- Example: `dim_customers`, `fact_sales`

---

## Glossary of Category Patterns
- `dim_` → Dimension table (e.g., `dim_products`)
- `fact_` → Fact table (e.g., `fact_sales`)
- `report_` → Report table (e.g., `report_customers`)

---

## Column Naming Conventions
- Surrogate Keys: `<table_name>_key` (e.g., `customer_key`)
- Technical Columns: `dwh_<column_name>` (e.g., `dwh_load_date`)

---

## Stored Procedures
- Pattern: `load_<layer>`
- Examples: `load_bronze`, `load_silver`, `load_gold`
