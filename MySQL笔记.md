数据库排名网站：https://db-engines.com/en/ranking



## 00.数据库基本知识

### 数据库基础

#### 数据库(DB)：

* 保存有组织的数据的容器（通常是一个文件或一组文件）。

* 数据库是一个以某种有组织的方式存储的**数据集合**

#### 数据库管理系统(DBMS)

* 数据的所有**存储**、**检索**、**管理**和**处理**实际上是由数据库软件——**DBMS**,

#### 表(table)

* 某种**特定类型数据的结构化清单**
* 表可以保存顾客清单、产品目录，或者其他信息清单。
* **如何存储**，如可以存储什么样的数据，数据**如何分解**，各部分信息**如何命名**

#### 列(column)

* **表中的一个字段**。所有表都是由一个或多个列组成的。

* 数据库中每个列都有相应的数据类型。数据类型定义列可以存储的数据种类。例如，如果列中存储的为数字（或许是订单中的物品数），则相应的数据类型应该为数值类型
* 数据类型（datatype） 所容许的数据的类型。每个表列都有相应的数据类型，它限制（或容许）该列中存储的数据。

#### 行(row)

* 表中的一个**记录(record)**。
* 在很大程度上，这**行和记录**是可以互相替代的

#### 主键(primary key)

* 表中每一行都应该有可以**唯一标识**自己的**一列（或一组列**）。
* 一个顾客表可以使用顾客编号列，而订单表可以使用订单ID.
*  虽然并不总是都需要主键，但大多数数据库设计人员都应保证他们创建的**每个表具有一个主键**，以便于
  以后的数据操纵和管理
* **主键要求**
  *  任意两行都**不具有相同**的主键值；
  *  **每**个**行都**必须具**有**一个主**键值**（主键列不允许NULL值）。

### MySQL简介

#### SQL（Structured Query Language）

* 结构化查询语言，专门用来与数据库通信的语言。
* 优点
  * 几乎所有重要的DBMS都支持SQL
  * 简单易学
  * 强有力，灵活，可以进行非常复杂和高级的数据库操作。

#### 什么是MySQL

* **MySQL是一种DBMS，即它是一种数据库软件**
* 优点
  * MySQL是**开放源代码**的，一般可以**免费**使用
  * **性能**——MySQL执行很快
  * **可信赖**——某些非常重要和声望很高的公司、站点使用MySQL，这些公司和站点都用MySQL来处理自己的重要数据。
  * **简单**——MySQL很容易安装和使用。

#### 客户机-服务器软件

* DBMS可分为两类：
  * 一类为**基于共享文件系统的DBMS**，
  * 一类为**基于客户机 — 服务器的DBMS**
* 与数据文件打交道的只有服务器软件

#### 开发工具

* mysql **命令行实用程序**
* **登入**： mysql - u username -p -h host -P port
* **帮助**：help
* **退出**: quit,  exit



改密码：





* 数据库系统解决的问题：持久化存储，优化读写，保证数据的有效性

* E-R关系模型
    * E表示entry，实体;  R表示relationship，关系
    * 一对一
    * 一对多
    * 多对多

* 常用的字段类型：
    * 数字：int,decimal(5, 2)
    * 字符串：char(定长字符串), varchar(变长字符串), text(不知道多大时用text)
    * 日期：datetime,date
    * 布尔：bit

* 约束
    * 主键: primary key  不重复唯一标识，查找速度非常快
    * 非空: not null
    * 惟一: unique  不重复
    * 默认: default
    * 外键: foreign key
    * auto_increment

## 01.安装和远程连接

### 安装

#### win10 安装 mysql

* win10 安装mysql: https://yq.aliyun.com/articles/642559

* mysql必知必会 创建样例表：https://blog.csdn.net/duhena0384/article/details/80396542

  注意**create.sql**和**populate.sql** 的文件编码要为utf-8

* win10 mysql服务开启和停止：管理员权限  运行：cmd -》 net start myql， net stop mysql

  * 或者win+R ,  services.msc, 查看服务进行关闭和开启

#### Ubuntu16.04 安装mysql

* sudo apt-get install mysql-server mysql-client
* 启动： sudo service mysql start
* 停止： sudo service mysql stop
* 重启： sudo service mysql restart

### 远程连接

#### navicat 远程连接mysql
* 安装navicat
* 找到mysql配置文件并修改
    * sudo vi /etc/mysql/mysql.conf.d/mysqld.cnf
    * 将默认的bind_address = 127.0.0.1 改为 0.0.0.0
* 登录mysql ，运行命令  
    * mysql -u root -p
    * grant all privileges on *.* to 'root'@'%' identified by 'xxxx';     xxx设置的mysql密码
    * flush privileges;
* 重启mysql
    * sudo service mysql restart
*  用navicat连接

#### 03.命令连接
* mysql -u root -p
    * 回车后输入密码
* exit或quit退出

#### 选择数据库

* USE 数据库名
* 如： USE crashcourse

### 03.select
* 查看版本：select version();
* 查看时间： select now();  
* 查看当前选择的数据库： select database();

### 05.数据库操作
* **查看所有数据库**：SHOW DATABASES;
* **查看当前选择的数据库**：SELECT DATABASE();
* **创建数据库**；CREATE DATABASE 数据库名  charset=utf8;
* **删除数据库**：DROP DATABASE 数据库名;
* **切换数据库**：USE 数据库名;
* SHOW ERRORS 和 SHOW WARNINGS ，用来显示服务器错误或警告消息
* SHOW GRANTS ，用来显示授予用户（所有用户或特定用户）的安
  全权限；
* SHOW CREATE DATABASE  数据库名 和SHOW CREATE TABLE 表名，分别用来显示创建特定数据库或表的MySQL语句；
*  SHOW STATUS ，用于显示广泛的服务器状态信息；

### 06.表操作
##### 查看包含有那些表:  SHOW TABLES;  

##### 创建表: create table 表名(列及类型);

* create table users (
  id int auto_increment primary key not null,
  username varchar(20) not null,
  passwd varchar(20)
  );

##### 删除表: drop table 表名;

##### 修改表: alter table 表名 add|modify|drop |change 列名 类型;

* alter table users add birthday datetime;
* alter table users change name username varchar(20);   # 该name为username
* alter table users modify name varchar(30);  # 该数据结构
* alter table users drop imag;  # 删除imag

##### 查看表结构：DESC 表名

* SHOW COLUMNS FROM 表名;

##### 更改表名称:  RENAME TABLE 原表名 To 新表名;

##### 查看表的创建语句: SHOW CREATE TABLE 表名;



### 07.插入查询等数据操作
##### 查询: select _column,_column from _table [where Clause] [limit N][offset M]

* 查看表的所有记录： select * from 表名;  
* 查看表的字段数据： select name from users;
* 查看表字段下条件数据（where）:  select * from students where isDelete=0;
* 查询表下字段范围数据(between): select * from students where id between 1 and 4;
* 查询表字段下固定条件数据:

##### 插入：insert into 表名(field1, field2,...fieldN) values (value1, value2,...valueN)[,(value1, value2, value3...)];

* insert into users
  (username, passwd, birthday)
  values
  ('xqy','123456',now());,
* 插入检索数据 INSERT INTO table_name (field1, field2, )  SELECT field1, field2 FROM table_name;

##### 删除: delete from 表名 where 条件;

* delete from users where id=3;

##### 修改：update 表名 set 列1=值1,... where 条件;

* update users set username='hxp', passwd='456' where id=2;



### 用户管理

#### 创建用户

```mysql
CREATE USER 'username'@'%' IDENTIFIED BY 'passwd'  
# localhost, %

```

#### 修改密码(mysql8.0)： 

```mysql
ALTER USER 'root'@'%'  IDENTIFIED WITH mysql_native_password BY 'new_passwd';

flush privileges

mysqladmin -u root -p旧密码 password 新密码   # p和旧密码之间没有空格
```






### 08.备份与恢复   
* 备份: sudo mysqldump -u root -p 数据库名 > ~/Desktop/back.sql
* 恢复：sudo mysql -u root -p 数据库名 < ~/Desktop/back.sql



SELECT

```mysql
SELECT 
    column_1, column_2, ...
FROM
    table_1
[INNER | LEFT |RIGHT] JOIN table_2 ON conditions
WHERE
    conditions
GROUP BY column_1
HAVING group_conditions
ORDER BY column_1
LIMIT offset, length;
```



DISTINCT  

```mysql
-- 语句
SELECT DISTINCT
    columns
FROM
    table_name
WHERE
    where_conditions;
 
-- 例子

SELECT DISTINCT
    lastname
FROM
    employees
ORDER BY lastname;

SELECT DISTINCT
    state
FROM
    customers;
    
-- distinct 有时可用group by替代
SELECT 
    state
FROM
    customers
GROUP BY state;

-- dinstinct修饰多个列时,  把(state,city)当做整体标识不同
SELECT DISTINCT
    state, city
FROM
    customers
WHERE
    state IS NOT NULL
ORDER BY state , city;

-- distinct 和sum,count等一起使用,可用来去重
SELECT 
    COUNT(DISTINCT state)
FROM
    customers
WHERE
    country = 'USA';

-- distinct和limit一起,但查找到limit数量时就停止
SELECT DISTINCT
    state
FROM
    customers
WHERE
    state IS NOT NULL
LIMIT 5;
```



ORDER BY 

```mysql
SELECT column1, column2,...
FROM tbl
ORDER BY column1 [ASC|DESC], column2 [ASC|DESC],...
-- 默认升序
-- 例子

-- order by
SELECT 
    contactLastname, contactFirstname
FROM
    customers
ORDER BY contactLastName;

-- desc逆序
SELECT 
    contactLastname, contactFirstname
FROM
    customers
ORDER BY contactLastName DESC;

-- 一个降,一个升
SELECT 
    contactLastname, contactFirstname
FROM
    customers
ORDER BY 
	contactLastName DESC,
	contactFirstname ASC;
    
-- 用于表达式
SELECT 
    ordernumber, 
    orderlinenumber, 
    quantityOrdered * priceEach as subtotal
FROM
    orderdetails
ORDER BY 
	quantityOrdered * priceEach DESC,
	ordernumber , 
	orderlinenumber;
    
-- field 用于自定义值的排序
SELECT 
    orderNumber, status
FROM
    orders
ORDER BY FIELD(status,
        'In Process',
        'On Hold',
        'Cancelled',
        'Resolved',
        'Disputed',
        'Shipped');
```



WHERE

```mysql

```

BETWEEN..AND

```
expr [NOT] BETWEEN begin_expr AND end_expr;
```



问题:

1.You should use the asterisk (*) for testing only. In practical, you  should list the columns that you want to get data explicitly because of the following reasons:

> - The asterisk (*) returns data from the columns that you may not use. It produces unnecessary I/O disk and network traffic between the MySQL database server and application.
> - If you explicit specify the columns, the result set is more predictable and easier to manage. Imagine when you use the asterisk(*) and someone [changes the table by adding more columns](http://www.mysqltutorial.org/mysql-alter-table.aspx), you will end up with a result set that is different from what you expected.
> - Using asterisk (*) may expose sensitive information to unauthorized users.

2.Difference between distinct and group by

> Generally speaking, the `DISTINCT` clause a special case of the `GROUP BY` clause. The difference between `DISTINCT` clause and `GROUP BY` clause is that the `GROUP BY` clause [sorts the result set](http://www.mysqltutorial.org/mysql-order-by/)whereas the `DISTINCT` clause does not.

