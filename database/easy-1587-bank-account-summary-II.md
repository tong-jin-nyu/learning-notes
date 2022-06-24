# 1587 Bank Account Summary II

Easy

Created on: 3/10/2021

Modified on: 6/23/2022

---

Table: `Users`

``` text
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

``` text
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
Amount is positive if the user received money and negative if they transferred money.
All accounts start with a balance 0.
```

Write an SQL query to report the name and balance of users with a balance higher than 10000. The balance of an account is equal to the sum of the amounts of all transactions involving that account.

Return the result table in any order.

---

``` sql
SELECT u.name, SUM(t.amount) AS balance
FROM Users AS u
JOIN Transactions AS t
ON u.account = t.account
GROUP BY t.account
HAVING SUM(t.amount) > 10000;
```

---
