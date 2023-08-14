**得学习一下group by的操作**
**datediff**
**CROSS JOIN 是什么东西**
**IFNULL**

    /*
    总结
    1.Group by 一定放在最后
    2.DateDiff 是绝对值
    3.日期可以直接比较，但是日期是''单引号内的
    */
    在 MySQL 中，`HAVING` 和 `WHERE` 是两个不同的子句，用于对查询结果进行筛选，但它们在使用时有一些区别。

1. `WHERE` 子句：
`WHERE` 子句用于在从表中检索数据之前对数据进行筛选。它在查询中出现在 `SELECT` 语句之前，用于指定行级条件，只返回满足条件的行。`WHERE` 子句过滤的是原始数据表中的行。

例如：
```sql
SELECT *
FROM orders
WHERE order_date >= '2023-01-01';
```
在上述示例中，只有 `order_date` 大于等于 '2023-01-01' 的订单会被返回。

2. `HAVING` 子句：
`HAVING` 子句用于在执行聚合函数（如 `SUM`、`COUNT`、`AVG` 等）之后对分组结果进行筛选。它在查询中出现在 `GROUP BY` 子句之后，用于指定分组级别的条件，只返回满足条件的分组。`HAVING` 子句过滤的是根据 `GROUP BY` 分组后的结果。

例如：
```sql
SELECT department, AVG(salary)
FROM employees
GROUP BY department
HAVING AVG(salary) > 50000;
```
在上述示例中，只有平均工资超过 50000 的部门才会被返回。

总结：
- `WHERE` 用于在检索数据之前对行级数据进行筛选，过滤的是原始数据表中的行。
- `HAVING` 用于在执行聚合函数后对分组级别的结果进行筛选，过滤的是分组后的结果。

注意：尽管 `HAVING` 子句可以在一些数据库中不使用 `GROUP BY` 子句而单独使用，但在标准 SQL 中，`HAVING` 通常与 `GROUP BY` 一起使用。