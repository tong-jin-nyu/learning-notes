# 608 Tree Node

Medium

https://leetcode.cn/problems/tree-node/

Created on: 5/27/2021

Modified on: 3/12/2023

---

Given a table `Tree`, `id` is identifier of the tree node and `p_id` is its 
parent node's id.

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

---

``` sql
SELECT 
    id, 
    CASE
        WHEN p_id IS NULL THEN 'Root'
        WHEN id IN (SELECT DISTINCT p_id FROM Tree) THEN 'Inner'
        ELSE 'Leaf'
    END AS type
FROM Tree;
```

``` sql
SELECT
    id,
    IF(p_id IS NULL,
        'Root',
        IF(id IN (SELECT DISTINCT p_id FROM Tree),
            'Inner',
            'Leaf')) AS type
FROM Tree
```

---

- `CASE WHEN`
- `IF`

