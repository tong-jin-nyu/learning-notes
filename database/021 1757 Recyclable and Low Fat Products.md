# LeetCode Notes - SQL

## 1757 Recyclable and Low Fat Products

Created on: 03/08/2021

Modified on: 03/08/2021

---

### Difficulty

Easy

## Instructions

Table: `Products`

```
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

## Solution (MySQL)

``` sql
SELECT product_id
FROM Products
WHERE low_fats = 'Y' AND
recyclable = 'Y';
```