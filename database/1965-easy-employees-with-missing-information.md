# 1965 Employees with Missing Information

Easy

https://leetcode.cn/problems/employees-with-missing-information/

Created on: 3/12/2023

Modified on: 3/12/2023

---

Table: `Employees`

```
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| employee_id | int     |
| name        | varchar |
+-------------+---------+
employee_id is the primary key for this table.
Each row of this table indicates the name of the employee whose ID is employee_id.
```

Table: `Salaries`

```
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| employee_id | int     |
| salary      | int     |
+-------------+---------+
employee_id is the primary key for this table.
Each row of this table indicates the salary of the employee whose ID is employee_id.
```

Write an SQL query to report the IDs of all the employees with missing 
information. The information of an employee is missing if:

- The employee's name is missing, or
- The employee's salary is missing.

Return the result table ordered by `employee_id` in ascending order.

The query result format is in the following example.


Example 1:

```
Input: 
Employees table:
+-------------+----------+
| employee_id | name     |
+-------------+----------+
| 2           | Crew     |
| 4           | Haven    |
| 5           | Kristian |
+-------------+----------+
Salaries table:
+-------------+--------+
| employee_id | salary |
+-------------+--------+
| 5           | 76071  |
| 1           | 22517  |
| 4           | 63539  |
+-------------+--------+
Output: 
+-------------+
| employee_id |
+-------------+
| 1           |
| 2           |
+-------------+
Explanation: 
Employees 1, 2, 4, and 5 are working at this company.
The name of employee 1 is missing.
The salary of employee 2 is missing.
```

---

``` sql
SELECT employee_id
FROM (
    SELECT e1.employee_id, name, salary
    FROM employees as e1
    LEFT JOIN salaries as s1
    ON e1.employee_id = s1.employee_id

    UNION

    SELECT s2.employee_id, name, salary
    FROM salaries as s2
    LEFT JOIN employees as e2
    ON s2.employee_id = e2.employee_id
) as t
WHERE name IS NULL OR salary IS NULL
ORDER BY employee_id
```

``` sql
SELECT employee_id
FROM (
    SELECT employee_id FROM employees
    UNION ALL
    SELECT employee_id FROM salaries
) as t
GROUP BY employee_id
HAVING COUNT(*) = 1
ORDER BY employee_id
```

---

- FULL OUTER JOIN
- GROUP BY then COUNT for IDs with more than 1 records