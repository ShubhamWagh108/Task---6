# 🛒 E-commerce Sales Trend Analysis (SQL)

This project analyzes monthly revenue and order volume trends using SQL on an e-commerce dataset. It helps derive business insights like total monthly revenue, number of orders, and overall sales performance over time.

---

## 📂 Dataset Overview

- **Source:** Kaggle / Custom e-commerce CSV
- **Table Name:** `e-commerce dataset`
- **Columns Used:**
  - `Order_Date` (text, e.g., "30-01-2018")
  - `Sales` (double)
  - Other columns like `Product`, `Customer_Id`, `Category`, etc.

---

## 🎯 Objective

- Extract year, month, and readable date (`Jan 2018`)
- Calculate:
  - Total revenue per month
  - Number of orders per month
- Group data and sort chronologically

---

## 🧾 SQL Code

```sql
SELECT 
    DATE_FORMAT(STR_TO_DATE(Order_Date, '%d-%m-%Y'), '%b %Y') AS month_year,
    YEAR(STR_TO_DATE(Order_Date, '%d-%m-%Y')) AS order_year,
    MONTH(STR_TO_DATE(Order_Date, '%d-%m-%Y')) AS order_month,
    SUM(Sales) AS total_revenue,
    COUNT(*) AS total_orders
FROM 
    `e-commerce dataset`
WHERE 
    Order_Date IS NOT NULL
GROUP BY 
    month_year, order_year, order_month
ORDER BY 
    order_year, order_month;
