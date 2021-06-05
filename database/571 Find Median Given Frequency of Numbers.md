# LeetCode Notes - SQL

## 571 Find Median Given Frequency of Numbers

Created on: 03/23/2021

Modified on: 03/23/2021

---

### Difficulty

Hard

## Instructions

The `Numbers` table keeps the value of number and its frequency.

```
+----------+-------------+
|  Number  |  Frequency  |
+----------+-------------|
|  0       |  7          |
|  1       |  1          |
|  2       |  3          |
|  3       |  1          |
+----------+-------------+
```

In this table, the numbers are `0, 0, 0, 0, 0, 0, 0, 1, 2, 2, 2, 3`, so the 
median is `(0 + 0) / 2 = 0`.

```
+--------+
| median |
+--------|
| 0.0000 |
+--------+
```
Write a query to find the median of all numbers and name the result as `median`.

## Solution

``` sql
SELECT
    ROUND(AVG(number), 4) AS median
FROM
    (
        SELECT
            number,
            SUM(frequency) OVER(ORDER BY number ASC) AS total_asc,
            SUM(frequency) OVER(ORDER BY number DESC) AS total_desc,
            SUM(frequency) OVER() AS total_sum
        FROM Numbers
        ORDER BY number ASC
    ) AS CTE
WHERE
    total_asc  >= total_sum / 2 AND
    total_desc >= total_sum / 2;
```

Create two columns of sum of frequency: one in ascending order as `total_asc`; 
the other in descending order as `total_desc`. Select the number(s) where the 
cumulative frequency is at the middle of both `total_asc` and `total_desc`. 
Finally, calculate the average (for both even and odd lengths) and round to 4 
decimal points.

## Note

- Window function
  - `SUM()`
  - `OVER()`