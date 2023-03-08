# 1667 Fix Names in a Table

Easy

https://leetcode.cn/problems/fix-names-in-a-table/

Created on: 3/5/2023

Modified on: 3/8/2023

---

Table: Users

```
+----------------+---------+
| Column Name    | Type    |
+----------------+---------+
| user_id        | int     |
| name           | varchar |
+----------------+---------+
user_id is the primary key for this table.
This table contains the ID and the name of the user. The name consists of only 
lowercase and uppercase characters.
```

Write an SQL query to fix the names so that only the first character is 
uppercase and the rest are lowercase.

Return the result table ordered by `user_id`.

The query result format is in the following example:

```
Input: 
Users table:
+---------+-------+
| user_id | name  |
+---------+-------+
| 1       | aLice |
| 2       | bOB   |
+---------+-------+
Output: 
+---------+-------+
| user_id | name  |
+---------+-------+
| 1       | Alice |
| 2       | Bob   |
+---------+-------+
```

## Solution (MySQL)

``` sql
SELECT user_id,
    CONCAT(UPPER(LEFT(name, 1)), LOWER(SUBSTR(name, 2))) AS name
FROM users
ORDER BY user_id
```

## Notes

`UPPER` and `LOWER`
`CONCAT`