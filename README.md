# 🛒 Zepto E-Commerce SQL Data Analysis

A structured SQL project analyzing product and inventory data from **Zepto**, an Indian quick-commerce grocery platform. This project covers the full data pipeline — from schema design and data cleaning to actionable business insights.

---

## 📁 Project Structure

```
zepto-sql-analysis/
│
├── Zepto_SQL_data_analysis.sql   # Main SQL script (exploration, cleaning, analysis)
└── README.md                     # Project documentation
```

---

## 🗄️ Dataset Overview

The dataset represents Zepto's product catalog with the following fields:

| Column | Type | Description |
|---|---|---|
| `sku_id` | SERIAL (PK) | Unique product identifier |
| `category` | VARCHAR | Product category |
| `name` | VARCHAR | Product name |
| `mrp` | NUMERIC | Maximum Retail Price |
| `discountPercent` | NUMERIC | Discount offered (%) |
| `availableQuantity` | INTEGER | Units available in stock |
| `discountedSellingPrice` | NUMERIC | Final selling price after discount |
| `weightInGms` | INTEGER | Product weight in grams |
| `outOfStock` | BOOLEAN | Stock availability flag |
| `quantity` | INTEGER | Pack quantity |

---

## 🧹 Data Cleaning

Before analysis, the following cleaning steps were applied:

- **Removed zero-price products** — entries where `mrp = 0` were deleted as they represent invalid or placeholder records.
- **Currency conversion** — prices were stored in paise (Indian subunit); converted to **rupees** by dividing by 100 for readability and accuracy.
- **Null value check** — all columns were screened for missing values to ensure data integrity.

---

## 📊 Analysis Questions & Insights

### Q1 — Top 10 Best-Value Products by Discount
Identified the products with the highest discount percentages to surface the best deals for customers.

### Q2 — High-MRP Products that are Out of Stock
Filtered premium products (MRP > ₹300) currently unavailable, helping flag high-priority restocking needs.

### Q3 — Estimated Revenue by Category
Calculated potential revenue per category using `discountedSellingPrice × availableQuantity` to identify the most revenue-generating segments.

### Q4 — Premium Products with Low Discounts
Found products priced above ₹500 with less than 10% discount — useful for promotional strategy adjustments.

### Q5 — Top 5 Categories by Average Discount
Ranked categories by average discount offered to understand which segments are most aggressively priced.

### Q6 — Price Per Gram (Value Analysis)
Computed cost efficiency (`discountedSellingPrice / weightInGms`) for products above 100g to identify the best deals by weight.

### Q7 — Product Weight Segmentation
Grouped products into tiers using `CASE` logic:
- **Low** — under 1,000g
- **Medium** — 1,000g to 4,999g
- **Bulk** — 5,000g and above

### Q8 — Total Inventory Weight Per Category
Summed `weightInGms × availableQuantity` per category to understand storage and logistics load distribution.

---

## 🛠️ Tools & Skills Used

- **Database**: PostgreSQL
- **Concepts**: DDL, DML, aggregation, filtering, `CASE` statements, `GROUP BY`, `HAVING`, subqueries, data type handling
- **Domain**: E-commerce, retail analytics, inventory management

---

## 💡 Key Takeaways

- Identified high-discount products and categories to support targeted marketing campaigns.
- Flagged out-of-stock premium items to prioritize inventory replenishment.
- Estimated category-level revenue to guide business investment decisions.
- Uncovered price-per-gram efficiency for competitive pricing benchmarking.

---

## 🚀 How to Run

1. Set up a PostgreSQL database.
2. Run the `Zepto_SQL_data_analysis.sql` script in order — the script handles table creation, data cleaning, and all analytical queries sequentially.
3. Review query outputs for insights.

---
