# LeetCode Notes - SQL

## 584 Find Customer Referee

Created on: 03/10/2021

Modified on: 03/29/2021

---

### Difficulty

Easy

## Instructions

Given a table `customer` holding customers information and the referee.

```
+------+------+-----------+
| id   | name | referee_id|
+------+------+-----------+
|    1 | Will |      NULL |
|    2 | Jane |      NULL |
|    3 | Alex |         2 |
|    4 | Bill |      NULL |
|    5 | Zack |         1 |
|    6 | Mark |         2 |
+------+------+-----------+
```

Write a query to return the list of customers **NOT** referred by the person with id `2`.

For the sample data above, the result is:

```
+------+
| name |
+------+
| Will |
| Jane |
| Bill |
| Zack |
+------+
```

## Solution

``` sql
SELECT name
FROM customer
WHERE referee_id <> 2 OR referee_id IS NULL;
```

## Note

- `IS NULL`