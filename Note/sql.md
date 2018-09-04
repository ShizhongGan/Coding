### SELECT queries 
``` sql
SELECT column, another_column, …          # 查询某行
FROM mytable;

SELECT *            # 查询全部列
FROM mytable;
```



#### Queries with constraints
```sql
SELECT column, another_column, …
FROM mytable
WHERE condition
    AND/OR another_condition
    AND/OR …;
```
