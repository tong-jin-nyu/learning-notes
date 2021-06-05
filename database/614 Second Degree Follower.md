# LeetCode Notes - SQL

## 614. Second Degree Follower

Created on: 05/31/2021

Modified on: 05/31/2021

---

### Difficulty

Medium

## Instructions

In facebook, there is a `follow` table with two columns: 

- **followee**
- **follower**

Please write a SQL query to get the amount of each followee's folloer if he/she 
has one.

For example:

```
+-------------+------------+
| followee    | follower   |
+-------------+------------+
|     A       |     B      |
|     B       |     C      |
|     B       |     D      |
|     D       |     E      |
+-------------+------------+
```

should output:

```
+-------------+------------+
| follower    | num        |
+-------------+------------+
|     B       |  2         |
|     D       |  1         |
+-------------+------------+
```

**Explanation**:

Both B and D exist in the follower list, when as a followee, B's follower is C 
and D, and D's follower is E. A does not exist in follower list.

**Note**:

Followee would not follow himself/herself in all cases.

Please display the result in follower's alphabet order.

## Solution (MySQL)

``` sql
SELECT
    followee AS follower,
    COUNT(DISTINCT follower) AS num
FROM follow
WHERE followee IN (SELECT DISTINCT follower FROM follow)
GROUP BY followee
ORDER BY follower ASC;
```

## Explanation

First, exclude those followees that do not exist in the follower list. Then, 
because a followee cannot follow himself/herself, we can just count the number 
of followers per followee.

Note that there might be duplicate records.

## Note

- CTE
  - `WHERE`