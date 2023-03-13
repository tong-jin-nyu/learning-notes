# 176 Second Highest Salary

Easy

Created on: 1/28/2021

Modified on: 3/12/2023

---

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

---

## Option 1

``` sql
SELECT MAX(salary) AS SecondHighestSalary
FROM Employee
WHERE salary <> (SELECT MAX(salary) FROM Employee)
```

Apply CTE as part of the `WHERE` clause. In the CTE, compute the highest salary. Then, selecting the maximum salary that is not equal to the highest salary gets the second highest salary.

---

## Option 2

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

Apply CTE as part of the `SELECT` clause. In the CTE, sort distinct salary value in descending order. Then, select the second value.

---

## Note

Option 1 is better at performance while option 2 is more genearlized.
