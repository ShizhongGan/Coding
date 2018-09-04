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
|Operator|	Condition|	SQL Example|
|=, !=, < <=, >, >=	|Standard numerical operators|	col_name != 4|
|BETWEEN … AND …|	Number is within range of two values (inclusive)|	col_name BETWEEN 1.5 AND 10.5|
|NOT BETWEEN … AND …|	Number is not within range of two values (inclusive)|	col_name NOT BETWEEN 1 AND 10|
|IN (…)	|Number exists in a list|	col_name IN (2, 4, 6)|
|NOT IN (…)	|Number does not exist in a list	|col_name NOT IN (1, 3, 5)|

