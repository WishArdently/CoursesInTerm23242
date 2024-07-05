## SQL

### 1. 查询

```sql
SELECT L
FROM R
WHERE C;
```

等价于：$\pi_L(\sigma_C(R))$

e.g. 

Movies(title, year, length, genre, studioName, producerC#)

SELECT title, year

FROM Movies

WHERE length = 256 AND studioName = 'Disney';

### 2. 模式匹配

```sql
s LIKE p
```

s是目标串，p为模式串，

% : 通配s中任意长的字符组合，也可以为空。 

_ : 通配s中任意一个字符



