# 175 Combine Two Tables

Easy

https://leetcode.cn/problems/combine-two-tables/

Created on: 1/28/2021

Modified on: 3/13/2023

---

Table: **Person**

| Column Name | Type      |
| ----------- | --------- |
| PersonId    | int       |
| FirstName   | varchar   |
| LastName    | varchar   |

---

Table: **Address**

| Column Name | Type      |
| ----------- | --------- |
| AddressId   | int       |
| PersonId    | int       |
| City        | varchar   |
| State       | varchar   |

---

Write a SQl query for a report that provides the following information for each person in the Person table, regardless if there is an address for each of those people:

`FirstName, LastName, City, State`

Example 1:

Input: 
Person table:
+----------+----------+-----------+
| personId | lastName | firstName |
+----------+----------+-----------+
| 1        | Wang     | Allen     |
| 2        | Alice    | Bob       |
+----------+----------+-----------+
Address table:
+-----------+----------+---------------+------------+
| addressId | personId | city          | state      |
+-----------+----------+---------------+------------+
| 1         | 2        | New York City | New York   |
| 2         | 3        | Leetcode      | California |
+-----------+----------+---------------+------------+
Output: 
+-----------+----------+---------------+----------+
| firstName | lastName | city          | state    |
+-----------+----------+---------------+----------+
| Allen     | Wang     | Null          | Null     |
| Bob       | Alice    | New York City | New York |
+-----------+----------+---------------+----------+
Explanation: 
There is no address in the address table for the personId = 1 so we return null in their city and state.
addressId = 1 contains information about the address of personId = 2.

---

``` sql
SELECT
    firstName,
    lastName,
    city,
    state
FROM Person AS p
LEFT JOIN Address AS a
ON p.personId = a.personId
```

---
