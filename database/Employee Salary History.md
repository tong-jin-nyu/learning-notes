# Others - SQL

## Employee Salary History

Created on: 03/24/2021

Modified on: 03/24/2021

### Question

You are given the following table containing historical employee salaries for company XYZ:

Table: **EmployeeSalaries**

employee_ID | salary | year
----------- | -----  | ----
1           | 80000 | 2020
1           | 70000 | 2019
1           | 60000 | 2018
2           | 65000 | 2020
2           | 65000 | 2019
2           | 60000 | 2018
3           | 65000 | 2019
3           | 60000 | 2018

Given the above table, can you write a SQL query to return the employees who have received at least 3 year over year raises based on the table's data?

### Solution

``` sql
SELECT
    employee_ID
FROM
    (
        SELECT
            employee_ID,
            salary,
            year,
            LAG(salary, 1) OVER(ORDER BY year) AS pre_1,
            LAG(salary, 2) OVER(ORDER BY year) AS pre_2
        FROM EmployeeSalaries
        GROUP BY employee_ID
        ORDER BY year DESC
    )
WHERE 
    COUNT(salary) >= 3 AND
    salary > pre_1 AND
    pre_1 > pre_2;
```




