# LeetCode Notes - SQL

## 550 Game Play Analysis IV

Created on: 03/10/2021

Modified on: 03/22/2021

---

### Difficulty

Medium

## Instructions

Table: `Activity`

```
+--------------+---------+
| Column Name  | Type    |
+--------------+---------+
| player_id    | int     |
| device_id    | int     |
| event_date   | date    |
| games_played | int     |
+--------------+---------+
(player_id, event_date) is the primary key of this table.
This table shows the activity of players of some game.
Each row is a record of a player who logged in and played a number of games (possibly 0) before logging out on some day using some device.
```

Write an SQL query that reports the **fraction** of players that logged in again on the day after the day they first logged in, **rounded to 2 decimal places**. In other words, you need to count the number of players that logged in for at least two consecutive days starting from their first login date, then divide that number by the total number of players.

The query result format is in the following example:

```
Activity table:
+-----------+-----------+------------+--------------+
| player_id | device_id | event_date | games_played |
+-----------+-----------+------------+--------------+
| 1         | 2         | 2016-03-01 | 5            |
| 1         | 2         | 2016-03-02 | 6            |
| 2         | 3         | 2017-06-25 | 1            |
| 3         | 1         | 2016-03-02 | 0            |
| 3         | 4         | 2018-07-03 | 5            |
+-----------+-----------+------------+--------------+

Result table:
+-----------+
| fraction  |
+-----------+
| 0.33      |
+-----------+
Only the player with id 1 logged back in after the first day he had logged in so the answer is 1/3 = 0.33
```

## Solution

``` sql
SELECT 
    ROUND(
        COUNT(DISTINCT player_id) / (SELECT COUNT(DISTINCT player_id) FROM Activity),
        2
    ) AS fraction
FROM Activity
WHERE (player_id, event_date) IN 
    (SELECT player_id, DATE(MIN(event_date) + 1) AS event_date
    FROM Activity
    GROUP BY player_id
    );
```

The fraction can be calculated as:

$$
\text{fraction} = \frac{\text{number of players logged in for at least 2 consecutive days}}{\text{total number of players}}
$$

Therefore, for the numerator, we need to count the number of distinct players in a dataset where they logged in for at least two consecutive days. For denominator, we can simply count the distinct players in the original dataset.

## Note

- Window function
  - CTE as part of the `SELECT` and `WHERE` clauses
- `ROUND()`
