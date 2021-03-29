# LeetCode Notes - SQL

## 579 Find Cumulative Salary of an Employee

Created on: 03/29/2021

Modified on: 03/29/2021

---

### Difficulty

Hard

## Instructions

The `Employee` table holds the salary information in a year. 

Write a SQL quert to get the cumulative sum of an employee's salary over a period of 3 months but exclude the most recent month.

The result should be displayed by `id` ascending, and then by `month` descending.

**Example**:

```
Input

| Id | Month | Salary |
|----|-------|--------|
| 1  | 1     | 20     |
| 2  | 1     | 20     |
| 1  | 2     | 30     |
| 2  | 2     | 30     |
| 3  | 2     | 40     |
| 1  | 3     | 40     |
| 3  | 3     | 60     |
| 1  | 4     | 60     |
| 3  | 4     | 70     |
Output
| Id | Month | Salary |
|----|-------|--------|
| 1  | 3     | 90     |
| 1  | 2     | 50     |
| 1  | 1     | 20     |
| 2  | 1     | 20     |
| 3  | 3     | 100    |
| 3  | 2     | 40     |
```

**Explanation**:

Employee `1` has 3 salary records for the following 3 months except the most recent month `4`: 
- salary 40 for month `3`
- salary 30 for month `2`
- salary 20 for month `1`

So the cumulative sum of salary of this employee over 3 months is 90 (40 + 30 + 20), 50 (30 + 20) and 20 respectively.

```
| Id | Month | Salary |
|----|-------|--------|
| 1  | 3     | 90     |
| 1  | 2     | 50     |
| 1  | 1     | 20     |
```

Employee `2` only has one salary record (month `1`) expect its most recent month `2`.

```
| Id | Month | Salary |
|----|-------|--------|
| 2  | 1     | 20     |
```

Employee `3` has two salary records except its most recent pay month `4`:
- month `3` with 60
- month `2` with 40

So the cumulative salary is as following:

```
| Id | Month | Salary |
|----|-------|--------|
| 3  | 3     | 100    |
| 3  | 2     | 40     |
```

## Solution

``` sql
SELECT 
    id,
    month,
    salary
FROM
    (SELECT
        id,
        month,
        SUM(salary) OVER(PARTITION BY id ORDER BY month ROWS 2 PRECEDING) AS salary,
        RANK() OVER(PARTITION BY id ORDER BY month DESC) AS rnk
    FROM Employee) AS CTE
WHERE rnk > 1
ORDER BY id ASC, month DESC;
```



## Note

- Window function
  - `SUM()`
  - `OVER()`
  - `RANK()`