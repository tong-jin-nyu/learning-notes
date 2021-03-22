# LeetCode Notes - SQL

## 184 Department Highest Salary

Created on: 01/30/2021

Modified on: 03/22/2021

---

### Difficulty

Medium

## Instructions

The `Employee` table holds all employees. Every employee has an id, a salary, and ther is also a column for the department id.


| Id | Name  | Salary | DepartmentId |
| -- | ----- | ------ | ------------ |
| 1  | Joe   | 70000  | 1            |
| 2  | Jim   | 90000  | 1            |
| 3  | Henry | 80000  | 2            |
| 4  | Sam   | 60000  | 2            |
| 5  | Max   | 90000  | 1            |

The `Department` table holds all departments of the company.

| Id | Name   |
| -- | ------ |
| 1  | IT     |
| 2  | Sales  |

Write a SQL query to find employees who have the highest salary in each of the departments. For the above tables, your SQL query should return the following rows (order of rows does not matter).

| Department | Employee | Salary |
| ---------- | -------- | ------ |
| IT         | Max      | 90000  |
| IT         | Jim      | 90000  |
| Sales      | Henry    | 80000  |

**Explanation:**

Max and Jim both have the highest salary in the IT department and Henry has the highest salary in the Sales department.

## Solution (MS SQL)

``` sql
WITH CTE AS (
    SELECT 
        d.Name AS Department,
        e.Name AS Employee,
        Salary,
        RANK() OVER(PARTITION BY d.Name ORDER BY Salary DESC) AS rank
    FROM Employee AS e
    LEFT JOIN Department AS d
    ON e.DepartmentId = d.Id
    WHERE d.Name IS NOT NULL;
)
SELECT 
    Department,
    Employee,
    Salary
FROM CTE
WHERE rank = 1;
```

First, join table together. Then, create a new column, `rank`, using the window function `RANK()`. Finally, select the row where rank equals 1.

## Note

- Window function
  - `RANK()`
  - `PARTITION()`