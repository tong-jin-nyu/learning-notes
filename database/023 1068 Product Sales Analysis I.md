# LeetCode Notes - SQL

## 1068 Product Sales Analysis I

Created on: 03/09/2021

Modified on: 03/09/2021

---

### Difficulty

Easy

## Instructions

Table: `Sales`

```
+-------------+-------+
| Column Name | Type  |
+-------------+-------+
| sale_id     | int   |
| product_id  | int   |
| year        | int   |
| quantity    | int   |
| price       | int   |
+-------------+-------+
(sale_id, year) is the primary key of this table.
product_id is a foreign key to Product table.
Note that the price is per unit.
```

Table: `Product`

```
+--------------+---------+
| Column Name  | Type    |
+--------------+---------+
| product_id   | int     |
| product_name | varchar |
+--------------+---------+
product_id is the primary key of this table.
```

Write an SQL query that reports the product_name, year, and price for each sale_id in the Sales table.

Return the resulting table in any order.

## Solution (MySQL)

``` sql
SELECT
    p.product_name,
    year,
    price
FROM Sales AS s
JOIN Product AS p
ON s.product_id = p.product_id;
```