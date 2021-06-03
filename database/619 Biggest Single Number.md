# LeetCode Notes - SQL

## 619. Biggest Single Number

Created on: 06/03/2021

Modified on: 06/03/2021

---

### Difficulty

Easy

## Instructions

Table `my_numbers` contains many numbers in column **num** including duplicated ones. Can you write a SQL query to find the biggest number, which only appears once.

```
+---+
|num|
+---+
| 8 |
| 8 |
| 3 |
| 3 |
| 1 |
| 4 |
| 5 |
| 6 |
```

For the sample data above, your query should return the following result:

```
+---+
|num|
+---+
| 6 |
```

**Note**:

If there is no such number, just output `NULL`.

## Solution (MySQL)

``` sql
SELECT IFNULL(NULL, MAX(num)) AS num
FROM (
    SELECT *
    FROM my_numbers
    GROUP BY num
    HAVING COUNT(num) = 1
) AS CTE;
```

## Note

- CTE