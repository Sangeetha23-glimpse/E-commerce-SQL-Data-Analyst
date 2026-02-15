🛒 Zepto E-commerce SQL Data Analyst Portfolio Project

SQL-Driven Data Analysis • MySQL • Business Insights

📌 Project Overview

This repository showcases a complete SQL-centric data analytics project based on Zepto e-commerce data. 
The goal is to extract insights from transactional datasets by performing data cleaning, loading databases, writing advanced SQL queries,
and deriving business-decision support metrics.

🔗 Project Presentation
https://gamma.app/docs/Zepto-E-commerce-SQL-Data-Analyst-Portfolio-Project-96ynexeycbejbel?mode=present#card-jqdve3r70s2d8oo

This project demonstrates:
Strong SQL querying skills
Relational database handling
Analytical problem solving with business context



🗂️ What’s Inside
Component	Description
Database Schema	Design and structure of Zepto e-commerce tables
Data Cleaning Scripts	Python/SQL scripts for preparing raw data
SQL Queries	Complex SQL queries addressing business problems
Insights & KPI Metrics	Key findings from data
Documentation & Report	Written analysis and interpretation
📦 Dataset Description

The Zepto e-commerce dataset includes:

Customer profiles
Product catalogs
Order and transaction history
Payment and delivery details
Time-based purchase behavior

The raw data was analyzed, cleaned, and converted into structured tables suitable for SQL operations.

🧹 Data Preparation

Before analysis, data was preprocessed to ensure accuracy and consistency.

Example steps:

Remove duplicates
Handle missing values
Standardize fields (dates, numeric values)
Create relational table structure for MySQL
Data cleaning scripts can be found in data_preparation/ directory.

🗄️ MySQL Database Setup
1. Connect to MySQL
CREATE DATABASE zepto_ecommerce;
USE zepto_ecommerce;

2. Create Tables
CREATE TABLE customers (
    customer_id INT PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(100),
    city VARCHAR(50),
    signup_date DATE
);

CREATE TABLE products (
    product_id INT PRIMARY KEY,
    product_name VARCHAR(150),
    category VARCHAR(100),
    price DECIMAL(10,2)
);

CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    customer_id INT,
    order_date DATE,
    total_amount DECIMAL(10,2),
    FOREIGN KEY (customer_id) REFERENCES customers(customer_id)
);

CREATE TABLE order_items (
    item_id INT PRIMARY KEY,
    order_id INT,
    product_id INT,
    quantity INT,
    FOREIGN KEY (order_id) REFERENCES orders(order_id),
    FOREIGN KEY (product_id) REFERENCES products(product_id)
);

🧠 SQL Analysis & Business Queries

Below are samples of key SQL queries used to extract business insights:

✅ 1. Top 10 Best-Selling Products
SELECT 
    p.product_name,
    SUM(oi.quantity) AS total_sold
FROM order_items oi
JOIN products p ON oi.product_id = p.product_id
GROUP BY p.product_name
ORDER BY total_sold DESC
LIMIT 10;

📅 2. Monthly Revenue Trend
SELECT 
    DATE_FORMAT(o.order_date, '%Y-%m') AS month,
    SUM(o.total_amount) AS monthly_revenue
FROM orders o
GROUP BY month
ORDER BY month;

💳 3. Payment Method Distribution
SELECT
    payment_method,
    COUNT(*) AS count_orders
FROM orders
GROUP BY payment_method;

👥 4. Top Active Customers (by spend)
SELECT 
    c.customer_id,
    c.name,
    SUM(o.total_amount) AS total_spend
FROM orders o
JOIN customers c ON o.customer_id = c.customer_id
GROUP BY c.customer_id, c.name
ORDER BY total_spend DESC
LIMIT 10;

📈 Key Insights

Through SQL analysis, the project highlights:

✔ Most profitable product categories
✔ Highest revenue months & seasonal patterns
✔ Customer purchase behavior trends
✔ High-value customer segments
✔ Opportunities for targeted retention strategies

These insights translate data into business decisions for growth and retention.

📌 How Recruiters Can Assess This Project

This project demonstrates:

Advanced SQL skills (aggregation, joins, filtering, grouping)

Database design & normalization

Analytical thinking with business context

Data interpretation into actionable insights

📁 Repository Structure
/
├── data_preparation/
│   ├── zepto_cleaning.ipynb
│   └── cleaned_data.csv
├── sql_scripts/
│   ├── schema.sql
│   ├── queries.sql
│   └── advanced_metrics.sql
├── insights/
│   └── analysis_report.md
├── README.md

🚀 How to Get Started
1️⃣ Clone the Repo
git clone https://github.com/Sangeetha23-glimpse/E-commerce-SQL-Data-Analyst.git
cd E-commerce-SQL-Data-Analyst

2️⃣ Load Data (Optional)

Import cleaned_data.csv into your MySQL database.

3️⃣ Run SQL Scripts
mysql -u your_user -p zepto_ecommerce < sql_scripts/schema.sql
mysql -u your_user -p zepto_ecommerce < sql_scripts/queries.sql

4️⃣ Explore Queries

Open advanced_metrics.sql to explore business-oriented queries.
