# LeetCode Notes - SQL

## 613. Shortest Distance in a Line

Created on: 03/10/2021

Modified on: 05/27/2021

---

### Difficulty

Easy

## Instructions

Table `point` holds the x coordinate of some points on x-axis in a plane, which 
are all integers.

Write a query to find the shortest distance between two points in these points.

```
| x   |
|-----|
| -1  |
| 0   |
| 2   |
```

## Solution (MySQL)

``` sql
SELECT (p1.x - p2.x) AS shortest
FROM 
    point AS p1,
    point AS p2
WHERE p1.x > p2.x
ORDER BY shortest ASC
LIMIT 1;
```