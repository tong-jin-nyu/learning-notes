# LeetCode Notes - SQL

## 596 Classes More Than 5 Students

Created on: 02/01/2021

Modified on: 02/01/2021

---

### Difficulty

Easy

## Instructions

There is a table `courses` with columns: **student** and **class**.

Please list out all classes which have more than or equal to 5 students.

For example, the table:

| student | class      |
| ------- | ---------- |
| A       | Math       |
| B       | English    |
| C       | Math       |
| D       | Biology    |
| E       | Math       |
| F       | Computer   |
| G       | Math       |
| H       | Math       |
| I       | Math       |

Should output:

| class |
| ----- |
| Math  |

## Solution (MS SQL)

``` sql
WITH CTE AS (
    SELECT class, COUNT(*) AS total
    FROM courses
    GROUP BY class
)
SELECT class
FROM CTE
WHERE total >= 5;
```