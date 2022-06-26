# 181 Employees Earning More Than Their Managers

Easy

Created on: 1/29/2021

Modified on: 6/25/2022

---

The `Employee` table holds all employees including their managers. Every employee has an Id, and their is also a column for the manager Id.

| Id | Name  | Salary | ManagerId |
| -- | ----- | ------ | --------- |
| 1  | Joe   | 70000  | 3         |
| 2  | Henry | 80000  | 4         |
| 3  | Sam   | 60000  | NULL      |
| 4  | Max   | 90000  | NULL      |

Given the `Employee` table, write a SQL query that finds out employees who earn more than their managers. For the above table, Joe is the only employee who earns more than his manager.

| Employee |
| -------- |
| Joe      |

---

``` sql
SELECT e.Name AS Employee
FROM Employee AS e
LEFT JOIN 
    (SELECT Id, Salary
     FROM Employee) AS m
ON e.ManagerId = m.Id
WHERE e.Salary > m.Salary;
```

---
