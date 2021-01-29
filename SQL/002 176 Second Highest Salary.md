# LeetCode Notes - SQL

## 176 Combine Two Tables

Created on: 01/28/2021

Modified on: 01/28/2021

---

### Difficulty

Easy

## Instructions

Write a SQL query to get the second highest salary from the `Employee` table.

| Id  | Salary |
| --- | ------ |
| 1   | 100    |
| 2   | 200    |
| 3   | 300    |

For example, given the above Employee table, the query should return `200` as the second highest salary. If there is no second highest salary, then the query should return `null`.

| SecondHighestSalary |
| ------------------- |
| 200                 |

## Solution

``` sql
SELECT MAX(Salary) AS SecondHighestSalary
FROM Employee
WHERE Salary != (SELECT MAX(Salary) FROM Employee)
```

Alternatively,

``` sql
SELECT IFNULL(
    (SELECT DISTINCT Salary
     FROM Employee
     ORDER BY Salary DESC
     LIMIT 1 OFFSET 1
    ),
    NULL
) AS SecondHighestSalary
```