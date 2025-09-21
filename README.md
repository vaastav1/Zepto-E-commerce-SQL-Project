# 🛒 Zepto E-commerce SQL Data Analyst Portfolio Project

This is a complete, real-world data analyst portfolio project based on an e-commerce inventory dataset scraped from Zepto
 — one of India’s fastest-growing quick-commerce startups. This project simulates real analyst workflows, from raw data exploration to business-focused data analysis.

This project is perfect for:

📊 Data Analyst aspirants who want to build a strong Portfolio Project for interviews and LinkedIn

📚 Anyone learning SQL hands-on

💼 Preparing for interviews in retail, e-commerce, or product analytics

## 📌 Project Overview

The goal is to simulate how actual data analysts in the e-commerce or retail industries work behind the scenes to use SQL to:

✅ Set up a messy, real-world e-commerce inventory database
✅ Perform Exploratory Data Analysis (EDA) to explore product categories, availability, and pricing inconsistencies
✅ Implement Data Cleaning to handle null values, remove invalid entries, and convert pricing from paise to rupees
✅ Write business-driven SQL queries to derive insights around pricing, inventory, stock availability, revenue and more

## 📁 Dataset Overview

The dataset was sourced from Kaggle and was originally scraped from Zepto’s official product listings. It mimics what you’d typically encounter in a real-world e-commerce inventory system.

Each row represents a unique SKU (Stock Keeping Unit) for a product. Duplicate product names exist because the same product may appear multiple times in different package sizes, weights, discounts, or categories to improve visibility – exactly how real catalog data looks.

Columns:

sku_id: Unique identifier for each product entry (Synthetic Primary Key)

name: Product name as it appears on the app

category: Product category like Fruits, Snacks, Beverages, etc.

mrp: Maximum Retail Price (originally in paise, converted to ₹)

discountPercent: Discount applied on MRP

discountedSellingPrice: Final price after discount (also converted to ₹)

availableQuantity: Units available in inventory

weightInGms: Product weight in grams

outOfStock: Boolean flag indicating stock availability

quantity: Number of units per package

## 🔧 Project Workflow
### 1. Database & Table Creation

Create a SQL table with appropriate data types:
```sql
CREATE TABLE zepto (
  sku_id SERIAL PRIMARY KEY,
  category VARCHAR(120),
  name VARCHAR(150) NOT NULL,
  mrp NUMERIC(8,2),
  discountPercent NUMERIC(5,2),
  availableQuantity INTEGER,
  discountedSellingPrice NUMERIC(8,2),
  weightInGms INTEGER,
  outOfStock BOOLEAN,
  quantity INTEGER
);
```
### 2. Data Import
Load the CSV into PostgreSQL using:.

 - If you're not able to use the import feature, write this code instead:
```sql
   \copy zepto(category,name,mrp,discountPercent,availableQuantity,
            discountedSellingPrice,weightInGms,outOfStock,quantity)
  FROM 'data/zepto_v2.csv' WITH (FORMAT csv, HEADER true, DELIMITER ',', QUOTE '"', ENCODING 'UTF8');
```
- Faced encoding issues (UTF-8 error), which were fixed by saving the CSV file using CSV UTF-8 format.

### 3. 🔍 Data Exploration

Count total records

View sample data

Check for null values

Identify distinct product categories

Compare in-stock vs out-of-stock products

Detect duplicate product names

### 4. 🧹 Data Cleaning

Remove rows where MRP or discounted price is zero

Convert mrp and discountedSellingPrice from paise to rupees

### 5. 📊 Business Insights

Find top 10 best-value products based on discount percentage

Identify high-MRP products that are out of stock

Estimate revenue per product category

Filter expensive products with minimal discounts

Rank top 5 categories with highest average discounts

Calculate price per gram to find value-for-money products

Group products by weight into Low, Medium, Bulk categories

Measure total inventory weight per category

## 🛠️ How to Use This Project

1. **Clone the repository**
   ```bash
   git clone https://github.com/vaastav1/zepto-SQL-data-analysis-project.git
   cd zepto-SQL-data-analysis-project

   ```
2. **Open zepto_SQL_data_analysis.sql**

    This file contains:

      - Table creation

      - Data exploration

      - Data cleaning

      - SQL Business analysis
  
3. **Load the dataset into pgAdmin or any other PostgreSQL client**

      - Create a database and run the SQL file

      - Import the dataset (convert to UTF-8 if necessary)

4. **Follow along with the YouTube video for full walkthrough. 👨‍💼**








## 💡 Thanks for checking out the project! Your support means a lot — feel free to star ⭐ this repo or share it with someone learning SQL.🚀

