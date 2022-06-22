# 1350 Students With Invalid Departments

Easy

Created on: 3/10/2021

Modified on: 6/21/2022

---

Table: `Departments`

``` text
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

``` text
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

---

``` sql
SELECT id, name
FROM Students
WHERE department_id 
NOT IN (SELECT id FROM Departments);
```
