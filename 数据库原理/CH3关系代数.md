## CH3 Relational Algebra关系代数

### 一、Definition

$R \to R'$

关系到关系的映射

### 二、Set operations 

$R$和$S$拥有相同的属性组，有序化的列。

#### 1. Union

$R\cup S$

```postgresql
(SELECT * FROM R) UNION (SELECT * FROM S);
```

#### 2. Intersection

$R\cap S$

```postgresql
(SELECT * FROM R) INTERSECT (SELECT * FROM S);
```

#### 3. Difference

$R-S$

```postgresql
(SELECT * FROM R) EXCEPT (SELECT * FROM S);
```

### 三、Query operations

#### 1. Selection

$\sigma_C(R)$

按条件选择元组

#### 2. projection

***关系代数自动去重

$\pi_{A_1,A_2,\cdots,A_n}(R)$

选择列

### 四、Binary operations

#### 1. Cartesian product

$R\times S$

```postgresql
SELECT * FROM R CROSS JOIN S; --等价于
SELECT * FROM R, S;
```

#### 2. Natural Join

$R \bowtie S$

```postgresql
SELECT * FROM R NATURAL JOIN S;
```



```python
init C to be None
for ta in tupleA:
    for tb in tupleB:
        if(ta and tb has the same part)
        	C.append(ta or tb - (ta and tb)) 
```



#### 3. Theta-Joins

$R \bowtie_C S = \sigma_C (R\times S)$

条件笛卡尔积，而不是条件自然连接

```postgresql
SELECT * FROM R INNER JOIN S ON <condition> 
```

### 五、Renaming

$\rho_{S(A_1,A_2,\cdots,A_n)}$

### 六、Basic operations

$R\cap S = R -(R-S)$

$R\bowtie_C S =\sigma_C(R\times S)$

$R\bowtie S=\pi_L(\sigma_C(R\times S))$

六个基本操作：

>1. Union
>2. Difference
>3. Selection
>4. Projection
>5. Product
>6. Renaming