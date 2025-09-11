# sql-keys-toy-dataset


This repository contains a small **three-table dataset** used in the article  
**[Primary vs. Foreign Keys in SQL: What Every Beginner Should Know (and How to Answer Interview Questions)](YOUR_ARTICLE_LINK_HERE)**.

The goal is to help beginners practice identifying **primary keys**, **foreign keys**, and **composite keys**—just as you would when inheriting a real-world database that has **no enforced constraints**.

## Files

| File | Description |
|------|------------|
| `customers.csv`     | One row per customer. Columns: `customer_id`, `first_name`, `last_name`, `email`. |
| `orders.csv`        | One row per order. Columns: `order_id`, `order_date`, `customer_id`. |
| `order_details.csv` | One row per product within an order. Columns: `order_id`, `product_id`, `quantity`, `price`. |

## Key Relationships (Conceptual)

Although the CSVs **do not include explicit primary/foreign key constraints**, the logical relationships are:

- **customers** (`customer_id`) ←→ **orders** (`customer_id`)  
- **orders** (`order_id`) ←→ **order_details** (`order_id`)  
- Composite primary key on **order_details** is (`order_id`, `product_id`).

These relationships are what you’ll discover and enforce through the exercises.

## How to Use

1. **Download or clone** this repository.  
2. Import the CSVs into your database of choice (PostgreSQL, MySQL, SQLite, etc.).  
3. Run the practice queries from the article, for example:
   ```sql
   SELECT COUNT(DISTINCT customer_id), COUNT(*) FROM customers;
   SELECT COUNT(DISTINCT order_id || '-' || product_id), COUNT(*) FROM order_details;

## Challenge Questions

Try these queries and analyses once you’ve loaded the CSVs into a database:

- **Identify primary and foreign keys** in all three tables.  
- **Find the top customers by revenue** (for example, in August 2025).  
- **Compare** `COUNT(DISTINCT order_id)` in `orders` vs. `order_details` to see how detail rows can affect counts.
