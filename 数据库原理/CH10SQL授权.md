## CH10 SQL Authorization SQL授权

### 一、Privileges

#### 1. 基本权限

- SELECT（查询）
- INSERT（插入）
- DELETE（删除）
- UPDATE（更新）
- REFERENCE
- USAGE
- TRIGGER
- EXECUTE
- UNDER

对视图的访问不需要权限。

#### 2. 语法

`WITH GRANT OPTION`可以让被授予权限的用户继续向别的用户授予权限。

```postgresql
GRANT <list of privileges> ON <relation or other objects> TO <list of authorization IDs>;

GRANT SELECT, UPDATE(price) ON Sells TO sally;
```

#### 3. 撤回

```postgresql
REVOKE <list of privileges>
ON <relation or other objects>
FROM <list of authorization IDs>

-- options
CASCADE 	-- 相关权限全部收回
RESTRICT 	-- 若该用户将权限传递给了别的用户，报错
```

### 二、Grant Diagrams

#### 1. 记号

Nodes = user

Edge $X\to Y$表示X给Y授权

$AP$	$A$有权限$P$

$P^*$	$P$ with grant option

$P^{**}$	$P$的持有者

#### 2. 画法

当$A$为$B$授权$P$时，从$AP^*$或者$AP^{**}$到$BP$（或者$BP^*$）画一条边。

若$Q$弱于$P$，则终点为$BQ^*$或者$BQ$

#### 3. 规则

用户C有权限Q仅当有一条从$XP^{**}$到$CQ^*$或$CQ^{**}$或$CQ$的路径，$P\ge Q$且$C$可以为$X$

#### 4. 撤回

如果$A$从$B$收回权限$P$，

CASCADE : 删除从$AP$到$BP$的边

RESTRICT : 如果有从$BP$始发的边，拒绝撤回操作



任何节点都必须有一条从**节点始发的路径，如果没有，自动删除。











