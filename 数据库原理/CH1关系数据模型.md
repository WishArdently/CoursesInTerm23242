## CH1 Relational Data Model

### 一、定义

#### 1. data model数据模型

data model  = Structure + Operations + Constrains

结构 + 操作 + 约束

#### 2. Relation 关系

Two-dimension table二维表格

#### 3. Attribute属性

列的名字

#### 4. Schema模式

关系名称和它的属性

> Movies(title, year, length, genre)

#### 5. Tuple元组

关系中的一行

>(Gone, 1939, 231, drama)

#### 6. Domain域

特定的数据类型，与属性关联

> Movies(title:string, year:integer, length:integer, genre:string)

#### 7. Key键

任意两个元组的键不相等

### 二、SQL表

#### 1. CREATE TABLE

```postgresql
CREATE TABLE movieexec(
	name CHAR(30),
	address VARCHAR(255),
    cert	INT PRIMARY KEY,	# 主键
	networth	INT
);
CREATE TABLE studio(
	name CHAR(50) PRIMARY KEY,
    address VARCHAR(255),
    presc INT,
    FOREIGN KEY (presc) REFERENCES movieexec(cert)	# 外键
);
```

#### 2. INSERT

```postgresql
INSERT INTO movieexec VALUES('aaa', 'bbb', 114514, 1919810);
```

#### 3. QUERY

```postgresql
SELECT *
FROM movies
WHERE studioname='Disney' AND year=1990
ORDER BY length, title;
```

#### 4. DROP

```postgresql
DROP TABLE R;
ALTER TABLE MovieStar ADD phone CHAR(16);
ALTER TABLE MovieStar DROP birthdate;
```

#### 5. 默认值

```postgresql
gender CHAR(1) DEFAULT '?';
birthdate DATE DEFAULT DATE '0000-00-00'
ALTER TABLE MovieStar ADD phone CHAR(16) DEFAULT 'unlisted';
```

### 三、数据类型

>1. CHAR(n) VARCHAR(n)
>2. BIT(n) BIT VARYING(n)
>3. BOOLEAN    *TRUE, FALSE, UNKNOWN*
>4. INT or INTERGER or SMALLINT (SHORTINT)
>5. FLOAT or REAL DOUBLE PRECISION DECIMAL(n, d) *(长度，小数) (6, 2)->1234.56*  
>  6. NUMERIC(n, d) 任意长度的数字，高精度
>7. DATE *1948-05-14*
>8. TIME *15:00:02.5*
>9. TIMESTAMP *1984-05-14 12:00:00*