# LeetCode Notes - SQL

## 612. Shortest Distance in a Plane

Created on: 05/29/2021

Modified on: 05/31/2021

---

### Difficulty

Medium

## Instructions

Table point_2d holds the coordinates (x,y) of some unique points (more than two) 
in a plane.

Write a query to find the shortest distance between these points rounded to 2 
decimals.
 
```
| x  | y  |
|----|----|
| -1 | -1 |
| 0  | 0  |
| -1 | -2 |
```

The shortest distance is 1.00 from point (-1,-1) to (-1,2). So the output 
should be:
 
```
| shortest |
|----------|
| 1.00     |
```

**Note**: The longest distance among all the points are less than 10000.

## Solution (MySQL)

``` sql
SELECT 
    ROUND(
        MIN(SQRT(POWER(p1.x - p2.x, 2) + POWER(p1.y - p2.y, 2))), 2
    ) AS shortest
FROM point_2d AS p1, point_2d AS p2
WHERE (p1.x, p1.y) <> (p2.x, p2.y);
```

## Explanation

The distance between two points can be calculated as:

$$
\text{distance} = \sqrt{(x_1 - x_2)^2 + (y_1 - y_2)^2}
$$

## Note

- `POWER`