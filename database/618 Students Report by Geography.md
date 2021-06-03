# LeetCode Notes - SQL

## 618. Students Report by Geography

Created on: 06/02/2021

Modified on: 06/02/2021

---

### Difficulty

Hard

## Instructions

A U.S. graduate school has students from Asia, Europe and America. The students' location information are stored in table `student` as below.

```
| name   | continent |
|--------|-----------|
| Jack   | America   |
| Pascal | Europe    |
| Xi     | Asia      |
| Jane   | America   |
```

Pivot the continent column in this table so that each name is sorted alphabetically and displayed underneath its corresponding continent. The ouptut headers should be America, Asia and Europe respectively. It is guaranteed that the student number from America is no less than either Asia or Europe.

For the sample input, the output is:

```
| America | Asia | Europe |
|---------|------|--------|
| Jack    | Xi   | Pascal |
| Jane    |      |        |
```

## Solution (MySQL)

``` sql
(SELECT *
FROM student) AS CTE
GROUP BY Continent
ORDER BY 

```

## Explanation

The hardest part of this problem is to convert date format in CTE.

## Note

- CTE as part of the main table
- `CASE`