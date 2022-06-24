# 1069 Product Sales Analysis II

Easy

Created on: 3/10/2021

Modified on: 6/23/2022

---

Table: `Sales`

``` text
+-------------+------+
| Column Name | Type |
+-------------+------+
| sale_id     | int   |
| product_id  | int   |
| year        | int   |
| quantity    | int   |
| price       | int   |
+-------------+-------+
sale_id is the primary key of this table.
product_id is a foreign key to Product table.
Note that the price is per unit.
```

Write an SQL query that reports the total quantity sold for every product id.

---

``` sql
SELECT 
    product_id, 
    SUM(quantity) AS total_quantity
FROM Sales
GROUP BY product_id;
```

---
