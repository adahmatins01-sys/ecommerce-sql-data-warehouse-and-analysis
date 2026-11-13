# Data Catalog for Gold Layer

## Overview
The Gold Layer is the business-level data representation, structured to support analytical and reporting use cases. It consists of dimension tables and fact tables for specific business metrics.

---

### gold.dim_customers
**Purpose:** Stores customer details enriched with demographic and geographic data.

**Columns:**
- `customer_key` (INT) – Surrogate key uniquely identifying each customer record.
- `customer_id` (INT) – Unique numerical identifier assigned to each customer.
- `customer_number` (NVARCHAR(50)) – Alphanumeric identifier for tracking.
- `first_name` (NVARCHAR(50)) – Customer’s first name.
- `last_name` (NVARCHAR(50)) – Customer’s last name.
- `country` (NVARCHAR(50)) – Country of residence.
- `marital_status` (NVARCHAR(50)) – Marital status.
- `gender` (NVARCHAR(50)) – Gender.
- `birthdate` (DATE) – Date of birth.
- `create_date` (DATE) – Record creation date.

---

### gold.dim_products
**Purpose:** Provides information about products and their attributes.

**Columns:**
- `product_key` (INT) – Surrogate key.
- `product_id` (INT) – Unique identifier.
- `product_number` (NVARCHAR(50)) – Alphanumeric product code.
- `product_name` (NVARCHAR(50)) – Descriptive product name.
- `category_id` (NVARCHAR(50)) – Category identifier.
- `category` (NVARCHAR(50)) – Product classification.
- `subcategory` (NVARCHAR(50)) – Detailed classification.
- `maintenance_required` (NVARCHAR(50)) – Maintenance flag.
- `cost` (INT) – Base price.
- `product_line` (NVARCHAR(50)) – Product line/series.
- `start_date` (DATE) – Availability date.

---

### gold.fact_sales
**Purpose:** Stores transactional sales data.

**Columns:**
- `order_number` (NVARCHAR(50)) – Unique order ID.
- `product_key` (INT) – Link to product dimension.
- `customer_key` (INT) – Link to customer dimension.
- `order_date` (DATE) – Order date.
- `shipping_date` (DATE) – Shipping date.
- `due_date` (DATE) – Payment due date.
- `sales_amount` (INT) – Total sale value.
- `quantity` (INT) – Units ordered.
- `price` (INT) – Price per unit.
