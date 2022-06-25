# 178 Rank Scores

Medium

Created on: 1/29/2021

Modified on: 6/25/2022

---

Write a SQL query to rank scores. If there is a tie between two scores, both should have the same ranking. Note that after a tie, the next ranking number should be the next consecutive integer value. In other words, there should be no "holes" between ranks.

Table `Scores`

``` text
| Id | Score     |
| -- | --------- |
| 1  | 3.50      |
| 2  | 3.65      |
| 3  | 4.00      |
| 4  | 3.85      |
| 5  | 4.00      |
| 6  | 3.65      |
```

For example, given the above `Scores` table, your query should generate the following report (order by highest score):

| Score | Rank  |
| ----- | ----- |
| 4.00  | 1     |
| 4.00  | 1     |
| 3.85  | 2     |
| 3.65  | 3     |
| 3.65  | 3     |
| 3.50  | 4     |

**Important Note**: For MySQL solutions, to escape reserved words used as column names, you can use an apostrophe before and after the keyword. For example \*`Rank`\*.

---

``` sql
SELECT 
    Score,
    DENSE_RANK() OVER(ORDER BY Score DESC) AS *RANK*
FROM Scores
ORDER BY Score DESC;
```

---

## Note

- Window function
- Difference between `DENSE_RANK()`, `RANK()` and `ROW_NUMBER()`
