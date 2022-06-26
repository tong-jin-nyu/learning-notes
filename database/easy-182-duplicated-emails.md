# 182 Duplicated Emails

Easy

Created on: 1/29/2021

Modified on: 6/25/2022

---

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

---

``` sql
SELECT Email
FROM Person
GROUP BY Email
HAVING COUNT(Email) > 1;
```

---
