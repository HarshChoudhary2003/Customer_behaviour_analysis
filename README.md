# Customer_behaviour_analysis
End-to-End Data Analytics Project using Python-SQL-Power BI
# 🛍️ Customer Shopping Behavior Analysis (MySQL + Power BI)

### 📊 Data-Driven Insights for E-Commerce Strategy

This project analyzes **customer shopping behavior** using transactional data from 3,900 purchases across various product categories.  
It aims to uncover insights into **spending patterns**, **product preferences**, **subscription behavior**, and **customer loyalty** — helping businesses make smarter, data-backed decisions.

---

## 📘 Project Overview

The project focuses on analyzing customer shopping data to:
- Understand purchasing patterns and demographics  
- Identify the top-performing products and categories  
- Study the impact of discounts and subscription programs  
- Compare revenue and engagement metrics across customer segments  
- Create an interactive dashboard for business insights  

---

## 🧾 Dataset Summary

| Attribute Type | Description |
|----------------|--------------|
| **Rows** | 3,900 |
| **Columns** | 18 |
| **Key Features** | Age, Gender, Location, Subscription Status, Purchase Amount, Item Purchased, Category, Season, Discount Applied, Review Rating, Shipping Type, Frequency of Purchases |
| **Missing Values** | 37 missing values in the `Review Rating` column (handled via median imputation) |

### Sample Columns:
- `Customer_ID`, `Gender`, `Age`, `Category`, `Item_Purchased`, `Purchase_Amount`, `Discount_Applied`, `Subscription_Status`, `Review_Rating`, `Shipping_Type`, `Previous_Purchases`, `Frequency_of_Purchases`

---

## 🧹 Data Preparation (Python)

Data preparation and feature engineering were performed in **Python** using libraries like **pandas**, **NumPy**, and **matplotlib**.

### Key Steps:
- Imported dataset with `pandas.read_csv()`
- Handled missing values in `Review_Rating` using category-wise median
- Renamed columns to `snake_case`
- Feature Engineering:
  - Created `age_group` column by binning ages
  - Created `purchase_frequency_days` for customer retention insights
- Dropped redundant columns like `promo_code_used`
- Verified data consistency and exported the cleaned dataset to MySQL

---

## 🗄️ Database Integration (MySQL)

Cleaned data was stored and analyzed in **MySQL**.

```sql
CREATE DATABASE customer_behaviour;
USE customer_behaviour;

CREATE TABLE customer_shopping_behavior (
    Customer_ID INT PRIMARY KEY,
    Gender VARCHAR(10),
    Age INT,
    Category VARCHAR(50),
    Item_Purchased VARCHAR(100),
    Purchase_Amount DECIMAL(10,2),
    Subscription_Status VARCHAR(15),
    Review_Rating DECIMAL(3,2),
    Shipping_Type VARCHAR(50),
    Frequency_of_Purchases VARCHAR(50),
    Previous_Purchases INT,
    Discount_Applied BOOLEAN
);
