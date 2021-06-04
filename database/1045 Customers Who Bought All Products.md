# LeetCode Notes - SQL

## 1045 Customers Who Bought All Products

Created on: 06/04/2021

Modified on: 06/04/2021

---

### Difficulty

Medium

## Instructions

Table: `Customer`

```
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| customer_id | int     |
| product_key | int     |
+-------------+---------+
product_key is a foreign key to Product table.
```

Table: `Product`

```
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| product_key | int     |
+-------------+---------+
product_key is the primary key column for this table.
```

Write an SQL query for a report that provides the customer ids from the `Customer` table that bought all the products in the `Product` table.

Return the result table in **any order**.

The query result format is in the following example:

```
Customer table:
+-------------+-------------+
| customer_id | product_key |
+-------------+-------------+
| 1           | 5           |
| 2           | 6           |
| 3           | 5           |
| 3           | 6           |
| 1           | 6           |
+-------------+-------------+

Product table:
+-------------+
| product_key |
+-------------+
| 5           |
| 6           |
+-------------+

Result table:
+-------------+
| customer_id |
+-------------+
| 1           |
| 3           |
+-------------+
The customers who bought all the products (5 and 6) are customers with id 1 and 3.
```

## Solution (MySQL)

``` sql
SELECT customer_id
FROM Customer
GROUP BY customer_id
HAVING COUNT(DISTINCT(product_key)) = (SELECT COUNT(*) FROM Product);
```

## Explanation

Group by customer_id and then count number of distinct product keys in each group. If there are equal number of distinct product keys in a certain group, than the customer associated with that group is considered to have purchased all products.

## Note

- `GROUP BY`
- `HAVING`