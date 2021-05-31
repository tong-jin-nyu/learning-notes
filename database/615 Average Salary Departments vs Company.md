# LeetCode Notes - SQL

## 615. Average Salary: Departments vs. Company

Created on: 05/31/2021

Modified on: 05/31/2021

---

### Difficulty

Hard

## Instructions

Given two tables as below, write a query to display the comparison result (higher/lower/same) of the average salary of employees in a department to the company's average salary.
 

Table: `salary`

```
| id | employee_id | amount | pay_date   |
|----|-------------|--------|------------|
| 1  | 1           | 9000   | 2017-03-31 |
| 2  | 2           | 6000   | 2017-03-31 |
| 3  | 3           | 10000  | 2017-03-31 |
| 4  | 1           | 7000   | 2017-02-28 |
| 5  | 2           | 6000   | 2017-02-28 |
| 6  | 3           | 8000   | 2017-02-28 |
```

The **employee_id** column refers to the **employee_id** in the following table `employee`.
 
```
| employee_id | department_id |
|-------------|---------------|
| 1           | 1             |
| 2           | 2             |
| 3           | 2             |
```

So for the sample data above, the result is:
 
```
| pay_month | department_id | comparison  |
|-----------|---------------|-------------|
| 2017-03   | 1             | higher      |
| 2017-03   | 2             | lower       |
| 2017-02   | 1             | same        |
| 2017-02   | 2             | same        |
```

**Explanation**:

In March, the company's average salary is (9000+6000+10000)/3 = 8333.33...
 
The average salary for department '1' is 9000, which is the salary of **employee_id** '1' since there is only one employee in this department. So the comparison result is 'higher' since 9000 > 8333.33 obviously.
 

The average salary of department '2' is (6000 + 10000)/2 = 8000, which is the average of **employee_id** '2' and '3'. So the comparison result is 'lower' since 8000 < 8333.33.
 

With the same formula for the average salary comparison in February, the result is 'same' since both the department '1' and '2' have the same average salary with the company, which is 7000.

## Solution (MySQL)

``` sql
SELECT 
    DISTINCT pay_month, 
    department_id,
    CASE
        WHEN company_avg > department_avg THEN 'lower'
        WHEN company_avg < department_avg THEN 'higher'
        ELSE 'same' 
    END AS comparison
FROM 
    (SELECT
        DATE_FORMAT(pay_date, '%Y-%m') AS pay_month,
        department_id,
        AVG(amount) OVER(PARTITION BY pay_date) AS company_avg,
        AVG(amount) OVER(PARTITION BY pay_date, department_id) AS department_avg
    FROM salary AS s
    JOIN employee AS e
    ON s.employee_id = e.employee_id) AS CTE
ORDER BY pay_month DESC;
```

## Explanation

The hardest part of this problem is to convert date format in CTE.

## Note

- CTE as part of the main table
- `CASE`