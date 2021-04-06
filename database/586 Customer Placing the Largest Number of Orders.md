# LeetCode Notes - SQL

## 586 Customer Placing the Largest Number of Orders

Created on: 03/31/2021

Modified on: 03/31/2021

---

### Difficulty

Easy

## Instructions

Table: `Orders`

```
+-----------------+----------+
| Column Name     | Type     |
+-----------------+----------+
| order_number    | int      |
| customer_number | int      |
+-----------------+----------+
order_number is the primary key for this table.
This table contains information about the order ID and the customer ID.
```

Write a SQL query to find the `customer_number` for the customer who has placed **the largest number of orders**.

It is guaranteed that exactly one customer will have placed more orders than any other customer.

The query result format is in the following example:

```
Orders table:
+--------------+-----------------+
| order_number | customer_number |
+--------------+-----------------+
| 1            | 1               |
| 2            | 2               |
| 3            | 3               |
| 4            | 3               |
+--------------+-----------------+

Result table:
+-----------------+
| customer_number |
+-----------------+
| 3               |
+-----------------+
The customer with number 3 has two orders, which is greater than either customer 1 or 2 because each of them only has one order.
So the result is customer_number 3.

**Follow up**: what if more than one customer have the largest number of orders, can you find all the `customer_number` in this case?

```
## Solution

``` sql
SELECT customer_number
FROM Orders
GROUP BY customer_number
ORDER BY COUNT(order_number) DESC
LIMIT 1;
```

## Follow-up Solution

```sql
SELECT customer_number
FROM Orders
GROUP BY customer_number
HAVING COUNT(order_number) >= ALL(
    SELECT COUNT(order_number)
    FROM Orders
    GROUP BY customer_number
);
```

The key is to apply nested search to find the `customer_number` whose total number of orders is greater than any of the remaining customer's.

## Notes

- `GROUP BY`
- `HAVING`
