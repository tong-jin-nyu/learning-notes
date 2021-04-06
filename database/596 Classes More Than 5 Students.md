# LeetCode Notes - SQL

## 596 Classes More Than 5 Students

Created on: 03/31/2021

Modified on: 03/31/2021

---

### Difficulty

Easy

## Instructions

There is a table courses with columns: student and class

Please list out all classes which have more than or equal to 5 students.

For example, the table:

```
+---------+------------+
| student | class      |
+---------+------------+
| A       | Math       |
| B       | English    |
| C       | Math       |
| D       | Biology    |
| E       | Math       |
| F       | Computer   |
| G       | Math       |
| H       | Math       |
| I       | Math       |
+---------+------------+
```

Should output:

```
+---------+
| class   |
+---------+
| Math    |
+---------+
```

**Note**:

The students should not be counted duplicate in each course.

## Solution

```sql
SELECT class
FROM courses
GROUP BY class
HAVING COUNT(DISTINCT student) >=5;
```

The key here is that some students may retake courses. Therefore, in the `HAVING` clause, we need to count distinct students.

### Notes

- `COUNT()`
- `DISTINCT()`
