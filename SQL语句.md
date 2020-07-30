# SQL语句

sql不区分大小写
SELECT - 更新数据库中提取数据
UPDATE -更新数据库中的数据
DELETE - 从数据库中删除数据
INSERT INTO - 向数据库中插入新数据
CREATE DATABASE - 创建新数据库
ALTER DATABASE - 修改数据库
CREATE TABLE - 创建新表
ALTER TABLE - 变更（改变）数据库表
DROP TABLE - 删除表
CREATE INDEX - 创建索引（搜索键）
DROP INDEX - 删除索引



## 查询语句

SELECT LastName FROM Persons
SELECT 列名称 FROM 表名称
SELECT * FROM Persons   #查询所有

### 查询过滤重复

SELECT DISTINCT 用于返回唯一不同的值。一个列如果有重复的字段，只显示一个
SELECT DISTINCT 列名称 FROM 表名称
SELECT DISTINCT Company FROM Orders 

### 多列表查询

SELECT LastName,FirstName FROM Persons

WHERE条件查询
SELECT 列名称 FROM 表名称 WHERE 列 运算符 值
SELECT * FROM Persons WHERE City='Beijing'
数值 不需要引号 

```
=	等于
<>	不等于
>	大于
<	小于
>=	大于等于
<=	小于等于
BETWEEN	在某个范围内
LIKE	搜索某种模式
```



## AND 运算符实例 或与非的与

SELECT * FROM Persons WHERE FirstName='Thomas' AND LastName='Carter'

## OR 运算符实例 或与非的或

SELECT * FROM Persons WHERE firstname='Thomas' OR lastname='Carter'

## 结合 AND 和 OR 运算符

SELECT * FROM Persons WHERE (FirstName='Thomas' OR FirstName='William')
AND LastName='Carter'

## AS 重命名

语法 SELECT 查询的数据 AS  重命名别的

SELECT M_NAME  AS  name

## ORDER BY 语句排序。

 order by 字段名 asc/desc  

    asc 表示升序  语句默认按照升序对记录进行排序。（默认为asc，可以省略）
    desc表示降序
order by 无法用于子查询，否则会报错
除非另外还指定了 TOP 或 FOR XML，否则，ORDER BY 子句在视图、内联函数、派生表、子查询和公用表表达式中无效。
SELECT Company, OrderNumber FROM Orders ORDER BY Company DESC, OrderNumber ASC

## INSERT INTO 表格插入新的行。

INSERT INTO 表名称(列1, 列2,...) VALUES (值1, 值2,....)
INSERT INTO table_name (列1, 列2,...) VALUES (值1, 值2,....)
在指定的列中插入数据，lastName和address是插入的字段 values是值
INSERT INTO Persons (LastName, Address) VALUES ('Wilson', 'Champs-Elysees')
多表插入
INSERT INTO 表名称 VALUES (值1, 值2,....);INSERT INTO 表名称 VALUES (值1, 值2,....)

### 有则更新，无则插入

INSERT INTO 表名(列1, 列2,...) 
VALUES (值1, 值2,....)
ON DUPLICATE KEY UPDATE 
列1= 'UpId',
列2= 'upPassword'，

INSERT INTO user_admin_t (_id,password) 
VALUES ('1','第一次插入的密码') 
ON DUPLICATE KEY UPDATE 
_id = 'UpId',
password = 'upPassword';

### 插入乱码

SELECT @字段 := ${db.NewID()} AS ID,
INSERT INTO 表名 (字段1} values (值1)
SELECT @M0004_ID:= ${db.NewID()) AS ID,
INSERT INTO 表名 (M0004_ID，name) values (@M0004_ID,'$input.name')

## UPDATE 语句 （修改信息,如果不设置WHERE条件，那么就更新所有的表 ）

UPDATE 表名
SET 设置的数据
WHERE 成立的条件

UPDATE Websites 
SET alexa='5000', country='USA' 
WHERE name='菜鸟教程';

## DELETE 删除语句

DELETE FROM 表名
WHERE 设立条件，不然会全部删除
DELETE FROM table_name
WHERE name="zhangsan"

## LIKE 搜索列中指定模式

SELECT * FROM 表名
WHERE 字段 LIKE 语句（‘G%’,'%K'，'oo'）
G%以G开头的   %K以K结尾的 oo包含oo的
SELECT * FROM weblist
WHERE name LIKE '%K'

## 通配符 

% 替代 0 个或多个字符 '%G' G开头 '%G%'  包含G的  'G%' G结尾的
_   替代一个字符 '_WEB'      web前面随意的一个字符
SELECT * FROM Websites
WHERE name LIKE 'G_o_le';

## 查询以什么开头的字段

SELECT * FROM Websites
WHERE name REGEXP '^[GFs]';   查询name以GFs三个开头的字段
SELECT * FROM Websites
WHERE name REGEXP '^[A-H]'; 查询以name从大写A到H开头的字段
SELECT * FROM Websites
WHERE name REGEXP '^[^A-H]';  查询以name不以A-H开头的字段

## IN允许在WHERE子句中规定多个值

SELECT * FROM Websites
WHERE name IN ('Google','菜鸟教程');  选取 name 为 "Google" 或 "菜鸟教程" 的字段

