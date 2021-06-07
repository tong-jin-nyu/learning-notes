# LeetCode Notes - SQL

## 1070. Product Sales Analysis III

Created on: 06/05/2021

Modified on: 06/05/2021

From: LeetCode (力扣)
Link: https://leetcode-cn.com/problems/product-sales-analysis-ii

---

### Difficulty

Medium

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
sale_id is the primary key of this table.
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

Write a SQL query that selects the **product_id**, **year**, **quantity**, and 
**price** for the **first year** of every product sold.

The query result format is in the following example:

```
Sales table:
+---------+------------+------+----------+-------+
| sale_id | product_id | year | quantity | price |
+---------+------------+------+----------+-------+ 
| 1       | 100        | 2008 | 10       | 5000  |
| 2       | 100        | 2009 | 12       | 5000  |
| 7       | 200        | 2011 | 15       | 9000  |
+---------+------------+------+----------+-------+

Product table:
+------------+--------------+
| product_id | product_name |
+------------+--------------+
| 100        | Nokia        |
| 200        | Apple        |
| 300        | Samsung      |
+------------+--------------+

Result table:
+------------+------------+----------+-------+
| product_id | first_year | quantity | price |
+------------+------------+----------+-------+ 
| 100        | 2008       | 10       | 5000  |
| 200        | 2011       | 15       | 9000  |
+------------+------------+----------+-------+
```

## Solution (MySQL)

``` sql
SELECT
    product_id,
    year AS first_year,
    quantity,
    price
FROM
    (SELECT *,
    RANK() OVER(PARTITION BY product_id ORDER BY year ASC) AS rnk
    FROM Sales) AS CTE
WHERE rnk = 1;
```

## Note

- CTE as part of the main table