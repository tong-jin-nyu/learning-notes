# LeetCode Notes - SQL

## 618. Students Report by Geography

Created on: 06/02/2021

Modified on: 06/02/2021

---

### Difficulty

Hard

## Instructions

A U.S. graduate school has students from Asia, Europe and America. The students' 
location information are stored in table `student` as below.

```
| name   | continent |
|--------|-----------|
| Jack   | America   |
| Pascal | Europe    |
| Xi     | Asia      |
| Jane   | America   |
```

Pivot the continent column in this table so that each name is sorted 
alphabetically and displayed underneath its corresponding continent. The ouptut 
headers should be America, Asia and Europe respectively. It is guaranteed 
that the student number from America is no less than either Asia or Europe.

For the sample input, the output is:

```
| America | Asia | Europe |
|---------|------|--------|
| Jack    | Xi   | Pascal |
| Jane    |      |        |
```

## Solution (MySQL)

``` sql
SELECT
    MAX(CASE WHEN continent = 'America' THEN name ELSE NULL END) AS America,
    MAX(CASE WHEN continent = 'Asia' THEN name ELSE NULL END) AS Asia,
    MAX(CASE WHEN continent = 'Europe' THEN name ELSE NULL END) AS Europe
FROM
    (SELECT *,
     ROW_NUMBER() OVER(PARTITION BY continent ORDER BY name) AS rnk
     FROM student
    ) AS CTE
GROUP BY rnk
```

## Explanation

First, create a ranking column to separate rows by continents. This will be the 
row number of the pivot table. Then, use case when function to mark the target 
name for each continent. This step also marks non-match rows as `NULL`. Finally, 
use aggregate function, `MAX()` (or `MIN()`), to exclude `NULL` values. `NULL` 
values will be replaced by blank space.

## Note

- Use aggregate function to exclude `NULL` values
  - `MAX()`
- Window Function
  - `ROW_NUMBER()`
  - `OVER()`
  - `PARTITION BY`