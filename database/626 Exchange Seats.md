# LeetCode Notes - SQL

## 626. Exchange Seats

Created on: 03/08/2021

Modified on: 06/04/2021

---

### Difficulty

Medium

## Instructions

Mary is a teacher in a middle school and she has a table `seat` storing 
students' names and their corresponding seat ids.

The column `id` is continuous increment.

Mary wants to change seats for the adjacent students.

Can you write a SQL query to output the result for Mary?

```
+---------+---------+
|    id   | student |
+---------+---------+
|    1    | Abbot   |
|    2    | Doris   |
|    3    | Emerson |
|    4    | Green   |
|    5    | Jeames  |
+---------+---------+

For the sample input, the output is:

+---------+---------+
|    id   | student |
+---------+---------+
|    1    | Doris   |
|    2    | Abbot   |
|    3    | Green   |
|    4    | Emerson |
|    5    | Jeames  |
+---------+---------+
```

## Solution (PostgreSQL)

``` sql
SELECT
    (CASE WHEN (id % 2) = 1 AND id <> (SELECT MAX(id)
                                       FROM seat) THEN id + 1
          WHEN (id % 2) = 0 THEN id - 1
          ELSE id END) AS id,
    student
FROM seat
ORDER BY id;
```

## Explanation

The best way to change seats for adjacent students is to swap odds with evens. 
Note that we need to skip the last students for odd number of students. 
This is because the last student in an odd row does not need to change seat.

## Note

- `CASE`