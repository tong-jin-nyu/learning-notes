# Customers Who Never Order

Easy

https://leetcode.cn/problems/customers-who-never-order/

Created on: 1/29/2021

Modified on: 2/28/2023

---

Suppose that a website contains two tables, the `Customers` table and the `Orders` table. 
Write a SQL query to find all customers who never order anything.

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

---

``` sql
SELECT name AS Customers
FROM Customers
WHERE id NOT IN (
    SELECT customerId 
    FROM Orders
)
```

``` sql
SELECT name AS Customers
FROM CUstomers AS c
LEFT JOIN Orders AS o ON c.Id = o.CustomerId
WHERE o.Id IS NULL
```

---

Both in-line table and LEFT JOIN work.