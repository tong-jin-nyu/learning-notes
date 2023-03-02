# 197 Rising Temperature

Created on: 2/1/2021

Modified on: 3/2/2023

Easy

https://leetcode.cn/problems/rising-temperature/

---

Table: `Weather`

| Column Name   | Type    |
| ------------- | ------- |
| id            | int     |
| recordDate    | date    |
| temperature   | int     |

`id is the primary key for this table.`

This table contains information about the temperature in a certain day.

Write an SQL query to find all dates' `id` with higher temperature compared to 
its previous dates (yesterday).

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

---

## Solution 1 (MS SQL Server)

``` sql
SELECT w2.id AS Id
FROM Weather AS w1
LEFT JOIN Weather AS w2
ON DATEDIFF(day, w1.recordDate, w2.recordDate) = 1
WHERE w1.Temperature < w2.Temperature;
```

Apply `DATEDIFF` to link days with their previous ones.

## Solution 2 (MySQL)

``` sql
SELECT w2.id
FROM weather as w1
LEFT JOIN weather as w2
ON DATEDIFF(w2.recordDate, w1.recordDate) = 1
WHERE w1.temperature < w2.temperature
```

## Solution 3

``` sql
SELECT id
FROM (
    SELECT
        id,
        recordDate,
        temperature,
        LAG(recordDate, 1) OVER(ORDER BY recordDate) AS last_date,
        LAG(temperature, 1) OVER(ORDER BY recordDate) AS last_temperature
    FROM Weather) AS a
WHERE 1=1 
  AND DATEDIFF(recordDate, last_date) = 1
  AND temperature > last_temperature
```

Apply `ROW_NUMBER()` as indices. Apply `LAG()` to select yesterday.

## Note

- `DATEDIFF`
- Window function
  - `ROW_NUMBER()`
  - `LAG()`