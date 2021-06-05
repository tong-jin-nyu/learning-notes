# LeetCode Notes - SQL

## 177 Nth Highest Salary

Created on: 01/29/2021

Modified on: 03/22/2021

---

### Difficulty

Medium

## Instructions

Write a SQL query to get the $n^{th}$ highest salary from the `Employee` table.

| Id  | Salary |
| --- | ------ |
| 1   | 100    |
| 2   | 200    |
| 3   | 300    |

For example, given the above Employee table, the $n^{th}$ highest salary where 
$n = 2$ is `200`. If there is no $n^{th}$ highest salary, then the query should 
return `null`.

| getNthHighestSalary(2) |
| ---------------------- |
| 200                    |

## Solution

``` sql
CREATE FUNCTION getNthHighestSalary(N INT) RETURNS INT
BEGIN
SET N = N-1;
  RETURN (
      # Write your MySQL query statement below.
      SELECT
        IFNULL(
          (SELECT DISTINCT Salary
           FROM Employee
           ORDER BY Salary DESC
           LIMIT 1 OFFSET N
          ),
          NULL
        )
  );
END
```

Similar to Problem 176, this problem asks to get the $n^{th}$ highest salary 
that is the second highest salary of the $(n - 1)^{th}$ (previous one).

## Note

- Replace OFFSET 1 with $N - 1$