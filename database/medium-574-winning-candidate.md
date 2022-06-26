# 574 Winning Candidate

Medium

Created on: 3/12/2021

Modified on: 6/25/2022

---

Table `Candidate`

``` text
+-----+---------+
| id  | Name    |
+-----+---------+
| 1   | A       |
| 2   | B       |
| 3   | C       |
| 4   | D       |
| 5   | E       |
+-----+---------+  
```

Table `Vote`

``` text
+-----+--------------+
| id  | CandidateId  |
+-----+--------------+
| 1   |     2        |
| 2   |     4        |
| 3   |     3        |
| 4   |     2        |
| 5   |     5        |
+-----+--------------+

id is the auto-increment primary key,
CandidateId is the id appeared in Candidate table.
```

Write a query to find the name of the winning candidate, the above example will return the winner `B`.

``` text
+------+
| Name |
+------+
| B    |
+------+
```

---

``` sql
SELECT name
FROM Candidate
WHERE id =
(
    SELECT candidateid
    FROM Vote
    GROUP BY candidateid
    ORDER BY COUNT(id) DESC
    LIMIT 1
);
```

---

## Note

For each unique candidate ID, find the number of wins. Then, sort in descending order and get the first row. Finally, link the candidate name with the winner ID.

- CTE as part of the `WHERE` clause
