# LeetCode Notes - SQL

## 578 Get Highest Answer Rate Question

Created on: 03/28/2021

Modified on: 03/28/2021

---

### Difficulty

Medium

## Instructions

Get the highest answer rate question from a table `survey_log` with these columns: 

- `id`: user id
- `action`: "show", "answer", "skip"
- `question_id`
- `answer_id`: not null when action column is "answer"; null for "show" and "skip"
- `q_num`: the numeral order of the question in current session.
- `timestamp`

Write a SQL query to identify the question which has the highest answer rate.

**Example**:

```
Input:
+------+-----------+--------------+------------+-----------+------------+
| id   | action    | question_id  | answer_id  | q_num     | timestamp  |
+------+-----------+--------------+------------+-----------+------------+
| 5    | show      | 285          | null       | 1         | 123        |
| 5    | answer    | 285          | 124124     | 1         | 124        |
| 5    | show      | 369          | null       | 2         | 125        |
| 5    | skip      | 369          | null       | 2         | 126        |
+------+-----------+--------------+------------+-----------+------------+
Output:
+-------------+
| survey_log  |
+-------------+
|    285      |
+-------------+
Explanation:
question 285 has answer rate 1/1, while question 369 has 0/1 answer rate, so output 285.
```

**Note**: the highest answer rate meaning is: answer number's ratio in show number in the same question. 


## Solution

``` sql
SELECT 
    question_id AS survey_log
FROM survey_log
WHERE answer_id IS NOT NULL
GROUP BY question_id
ORDER BY COUNT(answer_id) DESC
LIMIT 1;
```

The key is to transfer the highest answer rate. Getting the highest answer rate is equal to finding the question with highest answers. Therefore, we can count the number of answers in each question and then select the one with most answers.

## Note

- Logic