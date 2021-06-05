# LeetCode Notes - SQL

## 608 Tree Node

Created on: 05/27/2021

Modified on: 05/27/2021

---

### Difficulty

Medium

## Instructions

Given a table `tree`, **id** is identifier of the tree node and **p_id** is its 
parent node's **id**.

```
+----+------+
| id | p_id |
+----+------+
| 1  | null |
| 2  | 1    |
| 3  | 1    |
| 4  | 2    |
| 5  | 2    |
+----+------+
```

Each node in the tree can be one of three types:
- Leaf: if the node is a leaf node.
- Root: if the node is the root of the tree.
- Inner: if the node is neither a leaf node nor a root node.

Write a query to print the node id and the type of the node. Sort your output 
by the node id. The result of the above sample is:

```
+----+------+
| id | Type |
+----+------+
| 1  | Root |
| 2  | Inner|
| 3  | Leaf |
| 4  | Leaf |
| 5  | Leaf |
+----+------+
```

**Note**: If there is only one node on the tree, you only need to output its 
root attributes.

## Solution

```sql
SELECT 
    id AS Id, 
    CASE
        WHEN p_id IS NULL THEN 'Root'
        WHEN id IN (SELECT DISTINCT(p_id) FROM tree) THEN 'Inner'
        ELSE 'Leaf'
    END AS Type
FROM tree;
```

## Explanation

The goal is to count distinct ids. Therefore, we need to union two id columns 
together.

## Note

- `CASE`

