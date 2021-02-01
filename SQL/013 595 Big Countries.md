# LeetCode Notes - SQL

## 595 Big Countries

Created on: 02/01/2021

Modified on: 02/01/2021

---

### Difficulty

Easy

## Instructions

Table: `Weather`

| Column Name   | Type    |
| ------------- | ------- |
| id            | int     |
| recordDate    | date    |
| temperature   | int     |

id is the primary key for this table.

This table contains information about the temperature in a certain day.

Write an SQL query to find all dates' `id` with higher temperature compared to its previous dates (yesterday).

Return the result table in **any order**.

The query result format is in the following example:

| id | recordDate | Temperature |
| -- | ---------- | ----------- |
| 1  | 2015-01-01 | 10          |
| 2  | 2015-01-02 | 25          |
| 3  | 2015-01-03 | 20          |
| 4  | 2015-01-04 | 30          |

Result table:

| id |
| -- |
| 2  |
| 4  |

In 2015-01-02, temperature was higher than the previous day (10 -> 25).

In 2015-01-04, temperature was higher than the previous day (20 -> 30).

## Solution (MS SQL)

``` sql
SELECT w2.id AS Id
FROM Weather AS w1
LEFT JOIN Weather AS w2
ON DATEDIFF(day, w1.recordDate, w2.recordDate) = 1
WHERE w1.Temperature < w2.Temperature;
```

Alternatively,

``` sql
WITH cte_sorted AS
(
    SELECT *,
        ROW_NUMBER() OVER(ORDER BY recordDate ASC) AS row
    FROM Weather
)
SELECT id
FROM (
    SELECT *,
        LAG(Temperature, 1) OVER(ORDER BY row) AS temp_before,
        LAG(RecordDate, 1) OVER(ORDER BY row) AS date_before
    FROM cte_sorted) AS temp
WHERE DATEDIFF(day, date_before, RecordDate) = 1
    AND temp_before < Temperature;
```