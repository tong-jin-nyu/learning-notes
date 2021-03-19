# LeetCode Notes - SQL

## 1069. Product Sales Analysis II

Created on: 03/10/2021

Modified on: 03/10/2021

---

### Difficulty

Easy

## Instructions

Table: `Sales`

```
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

## Solution (MySQL)

``` sql
SELECT 
    product_id, 
    SUM(quantity) AS total_quantity
FROM Sales
GROUP BY product_id;
```