Created on: 01/25/2021

Modified on: 03/18/2021

# Reddit Post SQL

### Question

Suppose you're working for Reddit as an analyst. Reddit is trying to optimize its server allocation per subreddit, and you've been tasked with figuring out how much comment activity happens once a post is published.

Use your intuition to select a timeframe to query the data, as well as how you would want to present this information to the partnering team. The solution will be a SQL query with assumptions that you would need to state if this were asked in an interview. You have the following tables:

Table: **posts**

| Column Name  | Data Type | Description               |
| ------------ | --------- | ------------------------- |
| id           | integer   | id of the post            |
| publisher_id | integer   | id of the user posting    |
| score        | integer   | score of the post         |
| time         | integer   | post publish time in unix time |
| title        | string    | title of the post         |
| deleted      | boolean   | is the post deleted?      |
| dead         | boolean   | is the post active?       |
| subreddit_id | integer   | id of the subreddit       |

---

Table: **comments**

| ßColumn Name    | Data Type | Description               |
| -------------- | --------- | ------------------------- |
| id             | integer   | id of the comment         |
| author_id      | integer   | id of the commenter       |
| post_id        | integer   | id of the post the comment is nested under |
| parent_comment | integer   | id of parent comment that comment is nested under |
| deleted        | boolean   | is the comment deleted?   |

Given the above, write a SQL query to highlight comment activity by subreddit. This problem is intended to test how you can think through vague/open-ended questions.

### Solution

``` sql
SELECT DISTINCT 
  p.id as post_id,
  title,
  SUM(c.id) as n_comments,
FROM posts as p

LEFT JOIN comments as c
ON p.id = c.post_id
WHERE p.deleted = False AND 
      c.deleted = False AND
      p.dead = False AND
      EXTRACT(Month FROM time::date) BETWEEN 
```




