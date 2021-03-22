# LeetCode Notes - SQL

## 180 Consecutive Numbers

Created on: 01/30/2021

Modified on: 03/22/2021

---

### Difficulty

Medium

## Instructions

Table: `Logs`

| Column Name | Type    |
| ----------- | ------- |
| id          | int     |
| num         | varchar |

`id is the primary key for this table.`

Write a SQL query to find all numbers that appear at least three times consecutively. 

Return the result table in **any order**.

The query result format is in the following example: 

Logs table: 

| Id | Num |
| -- | --- |
| 1  | 1   |
| 2  | 1   |
| 3  | 1   |
| 4  | 2   |
| 5  | 1   |
| 6  | 2   |
| 7  | 2   |

Result table:

| ConsecutiveNums |
| --------------- |
| 1               |

`1 is the only number that appears consecutively for at least three times.`

## Solution 1
```sql
SELECT DISTINCT
    l1.Num AS ConsecutiveNums
FROM 
    Logs AS l1,
    Logs AS l2,
    Logs AS l3
WHERE
    l1.Id = l2.Id - 1
    AND l2.Id = l3.Id - 1
    AND l1.Num = l2.Num
    AND l2.Num = l3.Num
```

Self join table three times to include rows with three consecutive repeats. Use `DISTINCT` to get rid of duplicates.

## Solution 2

``` sql
WITH CTE AS (
    SELECT Num,
    LEAD(Num) OVER(ORDER BY Id) AS lead,
    LAG(Num) OVER(ORDER BY Id) AS lag
    FROM Logs
)
SELECT DISTINCT Num AS ConsecutiveNums
FROM CTE
WHERE Num = lead AND Num = lag;
```

Use window function `LEAD()` and `LAG()` to create two columns showing the lead and lag of a row. Filter to rows with same values as their leads and lags.

## Note

- Self join
- Window function
  - `LEAD()`
  - `LAG()`