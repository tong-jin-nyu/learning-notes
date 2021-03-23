# LeetCode Notes - SQL

## 569 Median Employee Salary

Created on: 03/22/2021

Modified on: 03/22/2021

---

### Difficulty

Hard

## Instructions

The `Employee` table holds all employees. The employee table has three columns: 

- Employee Id
- Company Name
- Salary

```
+-----+------------+--------+
|Id   | Company    | Salary |
+-----+------------+--------+
|1    | A          | 2341   |
|2    | A          | 341    |
|3    | A          | 15     |
|4    | A          | 15314  |
|5    | A          | 451    |
|6    | A          | 513    |
|7    | B          | 15     |
|8    | B          | 13     |
|9    | B          | 1154   |
|10   | B          | 1345   |
|11   | B          | 1221   |
|12   | B          | 234    |
|13   | C          | 2345   |
|14   | C          | 2645   |
|15   | C          | 2645   |
|16   | C          | 2652   |
|17   | C          | 65     |
+-----+------------+--------+
```

Write a SQL query to find the median salary of each company. Bonus points if you can solve it without using any built-in SQL functions.

```
+-----+------------+--------+
|Id   | Company    | Salary |
+-----+------------+--------+
|5    | A          | 451    |
|6    | A          | 513    |
|12   | B          | 234    |
|9    | B          | 1154   |
|14   | C          | 2645   |
+-----+------------+--------+
```

## Solution

``` sql
SELECT
    id,
    company,
    salary
FROM
    (
        SELECT
            id,
            company,
            salary,
            ROW_NUMBER() OVER(PARTITION BY company ORDER BY salary) AS rnk,
            COUNT(salary) OVER(PARTITION BY company) AS n_salary
        FROM Employee
    ) AS CTE
WHERE rnk IN (n_salary/2, n_salary/2 + 1, n_salary/2 + 0.5)
```

The fraction can be calculated as:

$$
\text{fraction} = \frac{\text{number of players logged in for at least 2 consecutive days}}{\text{total number of players}}
$$

Therefore, for the numerator, we need to count the number of distinct players in a dataset where they logged in for at least two consecutive days. For denominator, we can simply count the distinct players in the original dataset.

## Note

- Window function
  - `ROW_NUMBER()`
  - `PARTITION BY`
- Aggregation
  - median