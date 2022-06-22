# 1683 Invalid Tweets

Easy

Created on: 3/9/2021

Modified on: 6/21/2022

---

Table: `Tweets`

``` text
+----------------+---------+
| Column Name    | Type    |
+----------------+---------+
| tweet_id       | int     |
| content        | varchar |
+----------------+---------+
tweet_id is the primary key for this table.
This table contains all the tweets in a social media app.
```

Write an SQL query to find the IDs of the invalid tweets. The tweet is invalid if the number of characters used in the content of the tweet is strictly greater than 15.

Return the result table in any order.

---

``` sql
SELECT tweet_id
FROM Tweets
WHERE LENGTH(content) > 15;
```
