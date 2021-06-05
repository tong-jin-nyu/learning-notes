# LeetCode Notes - SQL

## 585 Investments in 2016

Created on: 03/29/2021

Modified on: 03/30/2021

---

### Difficulty

Medium

## Instructions

Write a SQL query to print the sum of all total investment values in 2016 
(`TIV_2016`) to a scale of 2 decimal places, for all policy holders who meet 
the following criteria:

1. Have the same `TIV_2015` value as one or more other policy holders
2. Are not located in the same city as any other policy holder 
   (i.e.: the (latitude, longitude) attribute pairs must be unique.)

**Input Format**:

The `insurance` table is described as follows:

```
| Column Name | Type          |
|-------------|---------------|
| PID         | INTEGER(11)   |
| TIV_2015    | NUMERIC(15,2) |
| TIV_2016    | NUMERIC(15,2) |
| LAT         | NUMERIC(5,2)  |
| LON         | NUMERIC(5,2)  |
```

where `PID` is the policy holder's policy ID, `TIV_2015` is the total 
investment value in 2015, `TIV_2016` is the total investment value in 2016, 
`LAT` is the latitude of the policy holder's city, and `LON` is the longtitude 
of the policy holder's city.

**Sample Input**:

```
| PID | TIV_2015 | TIV_2016 | LAT | LON |
|-----|----------|----------|-----|-----|
| 1   | 10       | 5        | 10  | 10  |
| 2   | 20       | 20       | 20  | 20  |
| 3   | 10       | 30       | 20  | 20  |
| 4   | 10       | 40       | 40  | 40  |
```

**Sample Output**:

```
| TIV_2016 |
|----------|
| 45.00    |
```

**Explanation**:

```
The first record in the table, like the last record, meets both of the two 
criteria.
The TIV_2015 value '10' is as the same as the third and forth record, and its 
location unique.

The second record does not meet any of the two criteria. Its TIV_2015 is not 
like any other policyholders.

And its location is the same with the third record, which makes the third record 
fail, too.

So, the result is the sum of TIV_2016 of the first and last record, which is 45.
```

## Solution

``` sql
SELECT
    SUM(TIV_2016) AS TIV_2016
FROM
    (
        SELECT
            TIV_2016,
            COUNT(PID) OVER(PARTITION BY TIV_2015) AS num_TIV,
            COUNT(PID) OVER(PARTITION BY LAT, LON) AS num_location
        FROM insurance
    ) AS CTE
WHERE
    CTE.num_TIV > 1 AND
    CTE.num_location = 1;
```

The key is to partition the data by `TIV_2015` and count number of `PID` with 
the same `TIV_2015`.
Then, do the same again for geographic location. Finally, select rows with the 
same `TIV_2015` value but with different `LAT` and `LON` values.

## Notes

- Window function
  - `PARTITION`
