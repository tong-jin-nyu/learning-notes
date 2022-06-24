# 175 Combine Two Tables

Easy

Created on: 1/28/2021

Modified on: 6/23/2022

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

---

``` sql
SELECT FirstName, LastName, City, State
FROM Person as p
LEFT JOIN Address as a
ON p.PersonId = a.PersonId;
```

---
