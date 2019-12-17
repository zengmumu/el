# MySQL 基本概念

## 数据库（database）

MySQL 是最流行的开源数据库系统，可运行于几乎所有的操作系统平台。在《[MySQL
安装](p-mysql_install.shtml)》一文中详解介绍了安装步骤，并且安装 PhpMyAdmin 来管理 MySQL 数据库系统。

在安装完 MySQL 数据库系统后，系统会默认创建一个名为 test
的数据库（database）。我们也可以创建多个数据库，但为了简单起见，我们暂定使用默认的 test 数据库，对应的数据库连接信息如下：

    
    
    主机：localhost
    数据库名：test
    账号：root
    密码：root123
    端口：3306
    

### 提示

通常支持数据库的主机供应商会提供给您一个数据库和一个账号供您使用，对应信息应该按照主机商提供的信息做修改。

## 数据表（table）

数据表（或称表）是数据库最重要的组成部分之一。数据库只是一个框架，数据表才是其实质内容，在数据库中存在一个或多个表。数据表是用来存储具体数据的对象，是有结构的数据的集合。

为减少数据输入错误，并能使数据库高效工作，表设计应按照一定原则对信息进行分类。同时为确保表结构设计的合理性，通常还要对表进行规范化设计，以消除表中存在的冗余，保证一个表只围绕一个主题，并使表容易维护。如用户信息表
user ，就记录用户的账户信息，而用户在论坛的发言或对文章的评论等，应该用另一个表记录。

数据表还有其他一些属性如“约束”、“索引”、“默认值”以及对应的数据结构等。

## 字段（field）

表由若干列构成，列也称为“字段”。每个字段必须指定一个名字，即字段名。字段名应该以标识字段的意义为宜，且须遵守SQL命名规范。

下面是一个表名为 user 表的例子：

uid | username | password | email | regdate  
---|---|---|---|---  
1 | admin | b7e591c246d010bb2ccd77d52490c85e | admin@5idev.com | 1277992339  
2 | 小明 | a193686a53e4de85ee3f2ff0576adf01 | xiao@163.com | 1278063917  
3 | Jack | 0193686a35e4de85ee3f2ff0567adf49 | jack@gmail.com | 1278061380  
  
在这个例子中，表一共有 5 个字段，分别为 uid、username、password、email 和 regdate。

## SQL 语言

SQL(Structured Query Language)
结构化查询语言，是一种数据库查询和程序设计语言，用于存取数据以及查询、更新和管理关系数据库系统。

SQL 语言包含4个部分：

  1. 数据定义语言(DDL)，例如：CREATE、DROP、ALTER 等语句
  2. 数据操作语言(DML)，例如：INSERT（插入）、UPDATE（修改）、DELETE（删除）语句
  3. 数据查询语言(DQL)，例如：SELECT 语句
  4. 数据控制语言(DCL)，例如：GRANT、REVOKE、COMMIT、ROLLBACK 等语句

MySQL 支持标准的 SQL 语句，也有自己私有的SQL语句。

## SQL 语言

SQL 数据基本操作分为为创建（create）、更新（update）、读取（read）和删除（delete），即 CURD
，以及在此基础上的更为复杂的一些数据操作。

  * create：分为 create 和 insert into ，用于创建数据库（表）以及向表里添加数据记录
  * update：更新数据库（表）信息以及更新表内的具体数据信息记录
  * read：读取数据库（表）信息以及表内的具体数据信息记录
  * delete：删除数据库（表）信息以及表内的具体数据信息记录

一个读取数据的例子：

    
    
    SELECT username FROM user
    

该语句表示从表 user 查询所有的用户名，得到的结果是一个查询返回的数据集，其结果可能如下：

username  
---  
admin  
小明  
Jack  
  
### 提示

SQL语句对大小写不敏感，SELECT username FROM user 与 select username from user 相同。
