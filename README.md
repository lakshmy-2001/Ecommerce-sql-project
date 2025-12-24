# 🛒 E-commerce SQL Business Analyst Project

This project simulates how data analysts in real-world e-commerce and retail environments work behind the scenes to explore, clean, and analyze inventory data using SQL. The goal is to replicate the messy, imperfect nature of production datasets and apply structured querying to uncover meaningful business insights.


## 📌 Project Overview
The objective of this project is to replicate how data analysts in e-commerce and retail organizations use SQL in real-world scenarios to work with imperfect, production-like data. Specifically, the project focuses on:

✅ Building and managing a messy, real-world e-commerce inventory database

✅ Conducting Exploratory Data Analysis (EDA) to analyze product categories, stock status, and pricing irregularities

✅ Applying data cleaning techniques to address missing values, eliminate invalid records, and standardize prices by converting them from paise to rupees

✅ Developing business-oriented SQL queries to extract actionable insights related to pricing strategies, inventory levels, stock availability, revenue potential, and overall product performance

The dataset was sourced from Kaggle and originally scraped from Zepto’s official product listings, making it a strong representation of a live e-commerce inventory system. Each row represents a unique SKU (Stock Keeping Unit). Duplicate product names exist intentionally, as the same product can appear multiple times across different package sizes, weights, discounts, or categories; exactly how real catalog data is structured to maximize visibility.

***Dataset Overview:***

The dataset contains product-level attributes such as category, pricing, discounts, availability, weight, and stock status. 

Each row represents a unique SKU (Stock Keeping Unit). Duplicate product names are expected, as the same product can appear multiple times across different package sizes, weights, discounts, or categories to enhance visibility, closely reflecting how real-world e-commerce catalogs are structured.


Key columns include:

🧾 Columns:
- **sku_id:** Unique identifier for each product entry (Synthetic Primary Key)

- **name:** Product name as it appears on the app

- **category:** Product category like Fruits, Snacks, Beverages, etc.

- **mrp:** Maximum Retail Price (originally in paise, converted to ₹)

- **discountPercent:** Discount applied on MRP

- **discountedSellingPrice:** Final price after discount (also converted to ₹)

- **availableQuantity:** Units available in inventory

- **weightInGms:** Product weight in grams

- **outOfStock:** Boolean flag indicating stock availability

- **quantity:** Number of units per package (mixed with grams for loose produce)




## 🔧 Project Workflow

### 1. Database & Table Creation

```sql
drop table if exists zepto;

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
The dataset is loaded in CSV format using pgAdmin's import feature.

### 2. 🔍 Data Exploration

- Calculated the total number of records to understand dataset size

- Inspected sample rows to get familiar with the data structure and attributes

- Checked all columns for missing or null values

- Listed all unique product categories present in the inventory

- Analyzed stock status by comparing available vs unavailable items

- Identified products appearing multiple times due to different SKUs

### 3. 🧹 Data Cleaning

- Removed invalid entries where MRP or final selling price was recorded as zero

- Standardized pricing by converting monetary values from paise to rupees for better interpretation

  
### 4. 📊 Business Insights

- Identified the top 10 products offering the highest discounts

- Flagged high-priced products that are currently out of stock

- Estimated potential revenue contribution across product categories

- Isolated premium products (MRP above ₹500) with low discount rates

- Ranked the top 5 categories based on average discount levels

- Calculated price per gram to identify value-for-money products

- Segmented products into Low, Medium, and Bulk weight groups

- Calculated total inventory weight at the category level

🎯 Key Takeaway

This project demonstrates end-to-end SQL analysis—from raw data ingestion and cleaning to generating actionable insights—closely mirroring the responsibilities of a data analyst working in the e-commerce or retail domain.
