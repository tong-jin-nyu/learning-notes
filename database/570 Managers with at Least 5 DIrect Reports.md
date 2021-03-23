# LeetCode Notes - SQL

## 570 Managers with at Least 5 Direct Reports

Created on: 03/22/2021

Modified on: 03/22/2021

---

### Difficulty

Medium

## Instructions

The `Employee` table holds all employees including their managers. Every employee has an Id, and there is also a column for the manager Id.

```
+------+----------+-----------+----------+
|Id    |Name 	  |Department |ManagerId |
+------+----------+-----------+----------+
|101   |John 	  |A 	      |null      |
|102   |Dan 	  |A 	      |101       |
|103   |James 	  |A 	      |101       |
|104   |Amy 	  |A 	      |101       |
|105   |Anne 	  |A 	      |101       |
|106   |Ron 	  |B 	      |101       |
+------+----------+-----------+----------+
```

Given the Employee table, write a SQL query that finds out managers with at least 5 direct report. For the above table, your SQL query should return:

```
+-------+
| Name  |
+-------+
| John  |
+-------+
```

## Solution

``` sql
SELECT e2.Name
FROM Employee AS e1, Employee AS e2
WHERE e1.ManagerId = e2.Id
GROUP BY e2.Id
HAVING COUNT(*) >= 5
```

Count managerId and select those distinct id with at least 5 duplicates. Then, self join to acquire manager names.

## Note

- `HAVING`
- `GROUP BY`