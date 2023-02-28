# 1757 Recyclable and Low Fat Products

Easy

Created on: 3/8/2021

Modified on: 2/28/2023

---

Table: `Products`

``` text
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| product_id  | int     |
| low_fats    | enum    |
| recyclable  | enum    |
+-------------+---------+
product_id is the primary key for this table.
low_fats is an ENUM of type ('Y', 'N') where 'Y' means this product is low fat and 'N' means it is not.
recyclable is an ENUM of types ('Y', 'N') where 'Y' means this product is recyclable and 'N' means it is not.
```

Write an SQL query to find the ids of products that are both low fat and recyclable.

Return the result table in any order.

---

``` sql
SELECT product_id
FROM Products
WHERE low_fats = 'Y' 
  AND recyclable = 'Y'
```
