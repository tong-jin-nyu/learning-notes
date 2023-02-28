# 584 Find Customer Referee

Easy

https://leetcode.cn/problems/find-customer-referee/

Created on: 3/10/2021

Modified on: 2/28/2023

---

Table: `Customer`

```
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| id          | int     |
| name        | varchar |
| referee_id  | int     |
+-------------+---------+
id is the primary key column for this table.
Each row of this table indicates the id of a customer, their name, and the id of the customer who referred them.
```

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

Write a query to return the list of customers **NOT** referred by the person 
with id `2`.

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

---

``` sql
SELECT name
FROM customer
WHERE (referee_id <> 2 OR referee_id IS NULL)
```

MySQL only solution`:

``` sql
SELECT name
FROM customer
WHERE NOT referee_id <=> 2
```

---

SQL uses three-way comparison so make sure to also evaluate `IS NULL` condition.