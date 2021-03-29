# LeetCode Notes - SQL

## 578 Get Highest Answer Rate Question

Created on: 03/28/2021

Modified on: 03/28/2021

---

### Difficulty

Medium

## Instructions

Get the highest answer rate question from a table `survey_log` with these columns: 

- `id`: user id
- `action`: "show", "answer", "skip"
- `question_id`
- `answer_id`: not null when action column is "answer"; null for "show" and "skip"
- `q_num`: the numeral order of the question in current session.
- `timestamp`

Table `Employee`

```
+-------+--------+-----------+--------+
| empId |  name  | supervisor| salary |
+-------+--------+-----------+--------+
|   1   | John   |  3        | 1000   |
|   2   | Dan    |  3        | 2000   |
|   3   | Brad   |  null     | 4000   |
|   4   | Thomas |  3        | 4000   |
+-------+--------+-----------+--------+

empId is the primary key column for this table.
```

Table `Bonus`

```
+-------+-------+
| empId | bonus |
+-------+-------+
| 2     | 500   |
| 4     | 2000  |
+-------+-------+

empId is the primary key column for this table.
```

Example ouput:

```
+-------+-------+
| name  | bonus |
+-------+-------+
| John  | null  |
| Dan   | 500   |
| Brad  | null  |
+-------+-------+
```

## Solution

``` sql
SELECT
    name,
    bonus
FROM Employee AS e
LEFT JOIN Bonus AS b
ON e.empId = b.empId
WHERE bonus < 1000 OR bonus IS NULL;
```

Use left join and `WHERE` to get the target values. Consider missing values (for those who do not have any bonus).

## Note

- `IS NULL`