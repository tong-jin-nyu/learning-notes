# LeetCode Notes - SQL

## 1350 Students With Invalid Departments

Created on: 03/10/2021

Modified on: 03/10/2021

---

### Difficulty

Easy

## Instructions

Table: `Departments`

```
+---------------+---------+
| Column Name   | Type    |
+---------------+---------+
| id            | int     |
| name          | varchar |
+---------------+---------+
id is the primary key for this table.
The table has information about the id of each department of a university.
```

Table: `Students`

```
+---------------+---------+
| Column Name   | Type    |
+---------------+---------+
| id            | int     |
| name          | varchar |
| department_id | int     |
+---------------+---------+
(id, unique_id) is the primary key for this table.
The table has information about the id of each student at a university and the id of the department he/she studies at.
```

Write an SQL query to find the id and the name of all students who are enrolled in departments that no longer exists.

Return the result table in any order.

## Solution (MySQL)

``` sql
SELECT id, name
FROM Students
WHERE department_id NOT IN (SELECT id FROM Departments);
```