# 196 Delete Duplicate Emails

Easy

https://leetcode.cn/problems/delete-duplicate-emails/

Created on: 1/31/2021

Modified on: 3/1/2023

---

Write a SQL query to delete all duplicate email entries in a table named 
`Person`, keeping only unique emails based on its smallest id.

| Id | Email                |
| -- | -------------------- |
| 1  | john@example.com     |
| 2  | bob@example.com      |
| 3  | john@example.com     |

Id is the primary key column for this table.

For example, after running your query, the above `Person` table should have 
the following rows:

| Id | Email            |
| -- | ---------------- |
| 1  | john@example.com |
| 2  | bob@example.com  |

Note:

Your output is the whole `Person` table after executing your sql. Use delete 
statement.

---

``` sql
DELETE p1
FROM person AS p1, person AS p2
WHERE 1=1
  AND p1.email = p2.email
  AND p1.id > p2.id
```

Use self join to keep identical rows. Filter to smaller IDs.

---

- Self join