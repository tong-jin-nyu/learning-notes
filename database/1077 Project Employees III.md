# LeetCode Notes - SQL

## 1077. Project Employees III

Created on: 06/06/2021

Modified on: 06/06/2021

---

### Difficulty

Medium

## Instructions

Table: `Project`

```
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| project_id  | int     |
| employee_id | int     |
+-------------+---------+
(project_id, employee_id) is the primary key of this table.
employee_id is a foreign key to Employee table.
```

Table: `Employee`

```
+------------------+---------+
| Column Name      | Type    |
+------------------+---------+
| employee_id      | int     |
| name             | varchar |
| experience_years | int     |
+------------------+---------+
employee_id is the primary key of this table.
```

Write an SQL query that reports the **most experienced** employees in each 
project. In case of a tie, report all employees with the maixmum of experience 
years.

The query result format is in the following example:

```
Project table:
+-------------+-------------+
| project_id  | employee_id |
+-------------+-------------+
| 1           | 1           |
| 1           | 2           |
| 1           | 3           |
| 2           | 1           |
| 2           | 4           |
+-------------+-------------+

Employee table:
+-------------+--------+------------------+
| employee_id | name   | experience_years |
+-------------+--------+------------------+
| 1           | Khaled | 3                |
| 2           | Ali    | 2                |
| 3           | John   | 3                |
| 4           | Doe    | 2                |
+-------------+--------+------------------+

Result table:
+-------------+---------------+
| project_id  | employee_id   |
+-------------+---------------+
| 1           | 1             |
| 1           | 3             |
| 2           | 1             |
+-------------+---------------+
Both employees with id 1 and 3 have the most experience among the employees of the first project. For the second project, the employee with id 1 has the most experience.
```

## Solution (MySQL)

``` sql
SELECT
    project_id,
    employee_id
FROM (
    SELECT 
        project_id,
        p.employee_id,
        RANK() OVER(PARTITION BY project_id ORDER BY experience_years DESC) AS 
        rnk
    FROM Project AS p
    JOIN Employee AS e
    ON p.employee_id = e.employee_id
) AS tmp
WHERE rnk = 1;
```

## Note

- `RANK()`