# 🗄️ SQL Relational Database & Sales Performance Analysis

## 📌 Business Scenario
This project demonstrates relational database creation, data normalization, and advanced querying in SQL. It models retail transaction records across multiple store branches and regions to extract revenue insights and transaction averages.

---

## 🛠️ Key SQL Techniques Applied
* **Schema Design & DDL:** Defined primary/foreign key relationships (`CREATE TABLE`, `FOREIGN KEY`).
* **Multi-Table Joins:** Integrated `Sales` and `Stores` entities using `INNER JOIN`.
* **Aggregations & Grouping:** Used `SUM()`, `COUNT()`, `AVG()`, and `GROUP BY` to summarize performance across categories and regions.
* **Sorting & Rounding:** Structured clean financial output using `ROUND()` and `ORDER BY`.

---

## 🔍 Key Business Insights

* **Top Revenue Region:** **South Region (London West)** led overall sales, driven primarily by high-value **Electronics** transactions (£890.00 average ticket size).
* **Highest Transaction Volume:** **Midlands (Birmingham Central)** recorded the most balanced distribution across Electronics, Clothing, and Beauty categories.
* **Category Performance:** **Electronics** maintained the highest Average Transaction Value across all store locations.

---

## 💻 Sample SQL Query
```sql
SELECT 
    st.Region,
    st.StoreName,
    s.Category,
    COUNT(s.TransactionID) AS Total_Transactions,
    SUM(s.Amount) AS Total_Revenue,
    ROUND(AVG(s.Amount), 2) AS Avg_Transaction_Value
FROM Sales s
JOIN Stores st ON s.StoreID = st.StoreID
GROUP BY st.Region, st.StoreName, s.Category
ORDER BY Total_Revenue DESC;
