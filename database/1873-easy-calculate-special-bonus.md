# 1873 Calculate Special Bonus

Easy

https://leetcode.cn/problems/calculate-special-bonus/

Created on: 3/1/2023

Modified on: 3/1/2023

---

Table: `Employees`

```
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| employee_id | int     |
| name        | varchar |
| salary      | int     |
+-------------+---------+
employee_id is the primary key for this table.
Each row of this table indicates the employee ID, employee name, and salary.
```

Write an SQL query to calculate the bonus of each employee. The bonus of an 
employee is 100% of their salary if the ID of the employee is an odd number 
and the employee name does not start with the character 'M'. 
The bonus of an employee is 0 otherwise.

Return the result table ordered by employee_id.

The query result format is in the following example.

```
Input: 
Employees table:
+-------------+---------+--------+
| employee_id | name    | salary |
+-------------+---------+--------+
| 2           | Meir    | 3000   |
| 3           | Michael | 3800   |
| 7           | Addilyn | 7400   |
| 8           | Juan    | 6100   |
| 9           | Kannon  | 7700   |
+-------------+---------+--------+
Output: 
+-------------+-------+
| employee_id | bonus |
+-------------+-------+
| 2           | 0     |
| 3           | 0     |
| 7           | 7400  |
| 8           | 0     |
| 9           | 7700  |
+-------------+-------+
Explanation: 
The employees with IDs 2 and 8 get 0 bonus because they have an even employee_id.
The employee with ID 3 gets 0 bonus because their name starts with 'M'.
The rest of the employees get a 100% bonus.
```

---

``` sql
SELECT
    employee_id,
    CASE
        WHEN MOD(employee_id, 2) <> 0 AND LEFT(name, 1) <> 'M' THEN salary 
        ELSE 0
    END AS bonus
FROM employees
ORDER BY employee_id
```

``` sql
SELECT
    employee_id,
    IF (employee_id % 2 = 1 AND name NOT LIKE 'M%', salary, 0) AS bonus
FROM employees
ORDER BY employee_id
```

``` sql
SELECT
    employee_id,
    CASE
        WHEN MOD(employee_id, 2) = 1 AND name NOT RLIKE '^M' THEN salary
        ELSE 0
    END AS bonus
FROM employees
ORDER BY employee_id
```

``` sql
SELECT
    employee_id,
    IF (employee_id & 1 AND name regexp '^[^M]', salary, 0) AS bonus
FROM employees
ORDER BY employee_id
```