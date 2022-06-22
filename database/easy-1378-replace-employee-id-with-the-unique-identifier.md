# 1378 Replace Employee ID With The Unique Identifier

Easy

Created on: 3/9/2021

Modified on: 6/21/2022

---

Table: `Employees`

``` text
+---------------+---------+
| Column Name   | Type    |
+---------------+---------+
| id            | int     |
| name          | varchar |
+---------------+---------+
id is the primary key for this table.
Each row of this table contains the id and the name of an employee in a company.
```

Table: `EmployeeUNI`

``` text
+---------------+---------+
| Column Name   | Type    |
+---------------+---------+
| id            | int     |
| unique_id     | int     |
+---------------+---------+
(id, unique_id) is the primary key for this table.
Each row of this table contains the id and the corresponding unique id of an employee in the company.
```

Write an SQL query to show the unique ID of each user, If a user doesn't have a unique ID replace just show null.

Return the result table in any order.

---

``` sql
SELECT unique_id, name
FROM Employees AS e
LEFT JOIN EmployeeUNI AS uni
ON e.id = uni.id;
```
