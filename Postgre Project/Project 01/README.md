# 🛍️ Retail Sales Analysis — SQL Project

## 📌 Project Overview

**Project Title**: Retail Sales Analysis  
**Level**: Beginner  
**Database**: `p1_retail_db`

Welcome to the **Retail Sales Analysis** project — a beginner-friendly SQL project that walks you through setting up a retail database, cleaning data, performing EDA, and answering real-world business questions using SQL. Perfect for aspiring **data analysts** who want to sharpen their SQL skills in a practical, hands-on way.

---

## 🎯 Project Objectives

1. 🗄️ **Set Up Database**: Create and populate the `p1_retail_db` retail database.  
2. 🧹 **Data Cleaning**: Identify and handle missing or null values.  
3. 📊 **Exploratory Data Analysis**: Get familiar with data structure and key metrics.  
4. 💼 **Business Insights**: Solve real business questions using SQL queries.

---

## 🧱 Project Structure

### 1️⃣ Database Setup

```sql
CREATE DATABASE p1_retail_db;

CREATE TABLE retail_sales
(
    transactions_id INT PRIMARY KEY,
    sale_date DATE,	
    sale_time TIME,
    customer_id INT,	
    gender VARCHAR(10),
    age INT,
    category VARCHAR(35),
    quantity INT,
    price_per_unit FLOAT,	
    cogs FLOAT,
    total_sale FLOAT
);
```
### 2️⃣ Data Exploration & Cleaning
1.🔢 Total Records

2.👤 Unique Customers

3.🛒 Product Categories

4.❌ Missing Values

```sql
-- Count total records
SELECT COUNT(*) FROM retail_sales;

-- Count distinct customers
SELECT COUNT(DISTINCT customer_id) FROM retail_sales;

-- List product categories
SELECT DISTINCT category FROM retail_sales;

-- Check for NULLs
SELECT * FROM retail_sales
WHERE 
    sale_date IS NULL OR sale_time IS NULL OR customer_id IS NULL OR 
    gender IS NULL OR age IS NULL OR category IS NULL OR 
    quantity IS NULL OR price_per_unit IS NULL OR cogs IS NULL;

-- Delete rows with missing values
DELETE FROM retail_sales
WHERE 
    sale_date IS NULL OR sale_time IS NULL OR customer_id IS NULL OR 
    gender IS NULL OR age IS NULL OR category IS NULL OR 
    quantity IS NULL OR price_per_unit IS NULL OR cogs IS NULL;
```
### 3️⃣ Business Queries & Insights
| 🔍 **Query**                | 💡 **Purpose**                            |
| --------------------------- | ----------------------------------------- |
| All sales on `2022-11-05`   | Identify transactions for a specific date |
| Clothing sales > 4 in Nov   | Analyze high-quantity sales for Clothing  |
| Sales per category          | Total & count of sales by category        |
| Avg age for Beauty buyers   | Understand demographic insights           |
| High-value sales > 1000     | Spot premium purchases                    |
| Gender-wise category sales  | Compare customer behavior                 |
| Best-selling month per year | Spot sales seasonality                    |
| Top 5 customers by sale     | Identify your VIP customers               |
| Unique buyers per category  | Gauge category popularity                 |
| Shift-wise order count      | See peak shopping hours                   |

**✅ Sample Queries:**
```sql
-- Total Sales per Category
SELECT category, SUM(total_sale) as net_sale, COUNT(*) as total_orders
FROM retail_sales
GROUP BY category;

-- Best-Selling Month Per Year
SELECT year, month, avg_sale
FROM (
    SELECT 
        EXTRACT(YEAR FROM sale_date) as year,
        EXTRACT(MONTH FROM sale_date) as month,
        AVG(total_sale) as avg_sale,
        RANK() OVER(PARTITION BY EXTRACT(YEAR FROM sale_date) ORDER BY AVG(total_sale) DESC) as rank
    FROM retail_sales
    GROUP BY 1, 2
) t
WHERE rank = 1;
```
## 📈 Key Findings

- **🧓 Demographics**: Customer age and gender data offer targeted marketing insights.  
- **💰 High-Value Sales**: Big-ticket purchases indicate premium product segments.  
- **📅 Seasonal Trends**: Sales peak in specific months; useful for stock planning.  
- **🎯 Customer Behavior**: Understand which gender buys which category and when.  
- **🏆 Top Customers**: Identify most valuable and loyal buyers.

## 📊 Reports Generated

- **🧾 Sales Summary**: Totals by category, customer, and region.  
- **📆 Trend Reports**: Month-wise performance and shift-based traffic.  
- **👥 Customer Insights**: Top buyers, unique customers per category.

## 🧠 Conclusion

This project is a great starting point for anyone learning **SQL for data analysis**. You'll learn how to:

- Clean and explore data 🧼🔍  
- Derive insights using real business cases 💼📉  
- Build confidence with hands-on SQL practice 💪  

> 📚 **Next Steps**: Try building visual dashboards or integrating with Python for advanced analytics!

## 🤝 Credits & Support

Created by wahid vinchenzo . 


