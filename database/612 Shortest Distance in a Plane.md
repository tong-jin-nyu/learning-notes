# LeetCode Notes - SQL

## 613. Shortest Distance in a Line

Created on: 05/27/2021

Modified on: 05/27/2021

---

### Difficulty

Medium

## Instructions

Table `point_2d` holds the coordinates (x, y) of some unique points (more than two) in a plane.

Write a query to find the shortest distance between these points rounded to 2 decimals.

```

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