# LeetCode Notes - SQL

## 183 Customers Who Never Order

Created on: 01/29/2021

Modified on: 01/29/2021

---

### Difficulty

Easy

## Instructions

Suppose that a website contains two tables, the `Customers` table and the `Orders` table. Write a SQL query to find all customers who never order anything.

Table: `Customers`

| Id | Name      |
| -- | --------- |
| 1  | Joe       |
| 2  | Henry     |
| 3  | Sam       |
| 4  | Max       |

---

Table: `Orders`

| Id | CustomerId |
| -- | ---------- |
| 1  | 3          |
| 2  | 1          |

Using the above tables as example, return the following: 

| Customers |
| --------- |
| Henry     |
| Max       |

## Solution

``` sql
SELECT Name as Customers
FROM Customers
WHERE Id NOT IN (
    SELECT CustomerId
    FROM Orders
);
```