# LeetCode Notes - SQL

## 1587. Bank Account Summary II

Created on: 03/10/2021

Modified on: 03/10/2021

---

### Difficulty

Easy

## Instructions

Table: `Users`

```
+---------------+---------+
| Column Name   | Type    |
+---------------+---------+
| account       | int     |
| name          | varchar |
+---------------+---------+
account is the primary key for this table.
Each row of this table contains the account number of each user in the bank.
```

Table: `Transactions`

```
+---------------+---------+
| Column Name   | Type    |
+---------------+---------+
| trans_id      | int     |
| account       | int     |
| amount        | int     |
| transacted_on | date    |
+---------------+---------+
trans_id is the primary key for this table.
Each row of this table contains all changes made to all accounts.
amount is positive if the user received money and negative if they transferred money.
All accounts start with a balance 0.
```

Write an SQL query to report the name and balance of users with a balance higher than 10000. The balance of an account is equal to the sum of the amounts of all transactions involving that account.

Return the result table in any order.

## Solution (MySQL)

``` sql
SELECT *
FROM
    (SELECT name, SUM(amount) AS balance
    FROM Users AS u
    JOIN Transactions AS t
    ON u.account = t.account
    GROUP BY t.account) AS CTE
WHERE CTE.balance > 10000;
```