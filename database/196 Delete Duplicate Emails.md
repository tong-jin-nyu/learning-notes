# LeetCode Notes - SQL

## 196 Delete Duplicate Emails

Created on: 01/31/2021

Modified on: 03/22/2021

---

### Difficulty

Easy

## Instructions

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

## Solution (MS SQL)

``` sql
DELETE p1
FROM Person AS p1,
Person AS p2
WHERE p1.Email = p2.Email AND p1.Id > p2.Id
```

Use self join to keep identical rows. Filter to smaller IDs.

## Note

- Self join