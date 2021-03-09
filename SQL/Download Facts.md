# Others - SQL

## Download Facts

Created on: 03/08/2021

Modified on: 03/08/2021

---

## Instructions

Table `user_dimension`

| Column Name | Type     |
| ----------- | -------- |
| user_id     | int      |
| account_id  | int      |

Table `account_dimension`

| Column Name     | Type     |
| --------------- | -------- |
| account_id      | int      |
| paying_customer | bool     |

Table `download_facts`

| Column Name | Type | 
| ----------- | ---- |
| date        | date |
| user_id     | int  |
| downloads   | int  |

Given three tables: `user_dimension`, `account_dimension`, and `download_facts`, find the average number of downloads for free vs paying customers broken out by day.

Note: The account_dimension table maps users to multiple accounts where they could be a paying customer or not. Also, round `average_downloads` to 2 decimal places.

### Output

| Column            | type  |
| ----------------- | ----- |
| date              | date  |
| paying_customer   | bool  |
| average_downloads | float |

## Solution (MS SQL)

``` sql
SELECT
    d.date,
    c.paying_customer,
    CAST(SUM(downloads) / COUNT(DISTINCT user_id) AS DECIMAL(10, 2)) AS average_downloads
FROM user_dimension AS u
INNER JOIN account_dimension AS a
ON u.account_id = a.account_id
LEFT JOIN download_facts AS d
ON u.user_id = d.user_id
GROUP BY date, paying_customer;
```