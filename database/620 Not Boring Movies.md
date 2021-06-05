# LeetCode Notes - SQL

## 620. Not Boring Movies

Created on: 03/08/2021

Modified on: 06/03/2021

---

### Difficulty

Easy

## Instructions

X city opened a new cinema, many people would like to go to this cinema. The 
cinema also gives out a poster indicating the movies’ ratings and descriptions.
Please write a SQL query to output movies with an odd numbered ID and a 
description that is not 'boring'. Order the result in descending order by 
rating.

For example, table `cinema`:

```
+---------+-----------+--------------+-----------+
|   id    | movie     |  description |  rating   |
+---------+-----------+--------------+-----------+
|   1     | War       |   great 3D   |   8.9     |
|   2     | Science   |   fiction    |   8.5     |
|   3     | irish     |   boring     |   6.2     |
|   4     | Ice song  |   Fantacy    |   8.6     |
|   5     | House card|   Interesting|   9.1     |
+---------+-----------+--------------+-----------+

For the example above, the output should be:

+---------+-----------+--------------+-----------+
|   id    | movie     |  description |  rating   |
+---------+-----------+--------------+-----------+
|   5     | House card|   Interesting|   9.1     |
|   1     | War       |   great 3D   |   8.9     |
+---------+-----------+--------------+-----------+

We have three movies with odd-numbered ID: 1, 3, and 5. The movie with ID = 3 
is boring so we don't include it in the answer.
```

## Solution (MySQL)

``` sql
SELECT *
FROM cinema
WHERE
    (id % 2) != 0 AND
    description != "boring"
ORDER BY rating DESC;
```

## Note

- `WHERE`