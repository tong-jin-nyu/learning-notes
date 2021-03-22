# LeetCode Notes - SQL

## 182 Duplicated Emails

Created on: 01/29/2021

Modified on: 03/22/2021

---

### Difficulty

Easy

## Instructions

Write a SQL query to find all duplicate emails in a table name `Person`.

| Id | Email     |
| -- | --------- |
| 1  | a@b.com   |
| 2  | c@d.com   |
| 3  | a@b.com   |

For example, your query should return the following for the above table:

| Email   |
| ------- |
| a@b.com |

**Note**: All emails are in lowercase.

## Solution

``` sql
SELECT Email
FROM Person
GROUP BY Email
HAVING COUNT(Email) > 1;
```

## Note

- `HAVING` is used for filtering aggregated metrics.