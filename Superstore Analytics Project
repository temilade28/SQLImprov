# 🏬 Superstore SQL Analysis Project

This project demonstrates my ability to explore and summarize retail product data using structured SQL queries. The dataset represents a simplified **superstore inventory**, with information about product categories, pricing, stock levels, and customer ratings.

---

## 📁 Dataset Overview

The dataset is created in a `superstore` table with the following schema:

```sql
CREATE TABLE superstore (
    item_id INTEGER PRIMARY KEY,
    item_name TEXT,
    category TEXT,
    price DECIMAL(10, 2),
    stock_quantity INTEGER,
    average_rating DECIMAL(3, 2)
);
```

Sample data includes 15 retail items across categories like **Kitchen Supplies**, **Furnishings**, **Electronics**, and **Appliances**.

---

## 🧠 Objective

Use SQL to:
- Sort and filter inventory
- Compute descriptive statistics (sum, average, min, max, count)
- Extract actionable insights on pricing, stock, and customer ratings

---

## 🛠️ SQL Queries & Key Insights

### 1. 📦 Items Ordered by Price
```sql
SELECT item_name, price
FROM superstore
ORDER BY price;
```

➡ **Insight**: Product prices range from **$24.99** to **$549.00**. The most expensive item is the Smart LED TV.

---

### 2. 💰 Total Price of All Items
```sql
SELECT SUM(price) FROM superstore;
```
- **Total value of products**: **$2,135.29**

---

### 3. 📉 Price Statistics
```sql
SELECT AVG(price), MAX(price), MIN(price), COUNT(price)
FROM superstore;
```

➡ **Insight**: The average product price is **$142.35**, with 15 products in total.

---

### 4. 🧂 Inventory in Kitchen Supplies Category
```sql
SELECT SUM(stock_quantity)
FROM superstore
WHERE category = 'Kitchen Supplies';
```

- **Total stock quantity for Kitchen Supplies**: **220 units**

---

### 5. ⭐ Products by Average Rating (Descending)
```sql
SELECT average_rating, item_name
FROM superstore
ORDER BY average_rating DESC;
```

➡ **Insight**: The **highest-rated item** is the *Premium Coffee Maker* with a **4.9** average rating.

---

## 📌 Skills Demonstrated

- SQL Data Exploration  
- Aggregations: `SUM()`, `AVG()`, `MIN()`, `MAX()`, `COUNT()`  
- Sorting & Filtering  
- Business insight derivation from tabular data

---

## 🔗 Resources
- [SQL Demo on DB Fiddle](https://www.db-fiddle.com/f/PvBAaQwEUSWAxZCsg4Vmx/0)
- Tools used: SQLite
