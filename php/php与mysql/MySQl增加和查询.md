# MySQL mysql_query 函数执行SQL语句
## INSER INTO

INSERT INTO 语法用于向数据表中添加数据记录。

语法： 

```mysql

INSERT INTO tb_name (column1, column2,...) VALUES (value1, value2,...)

```

下面的例子向 user 表添加一条记录： 

```

INSERT INTO user(username, password, email, regdate)VALUES('小王', 'zmm123', '12345@163.com', $regdate)

```

## 普通查询

SELECT FROM 语法用于从数据表中查询读取数据。  

 

语法： 

```

SELECT column1,column1,... FROM tb_name

```

如果要读取全部字段，可以使用 * 号代替字段名： 

```

SELECT * FROM tb_name

```

下面例子 获取用户表里面所有信息

```

SELECT * FROM user;

```

## WHERE 条件

有时候操作数据库时，只操作一些有条件限制的数据，这时可以在SQL语句中添加WHERE子句来规定数据操作的条件。

语法：

    
    
    SELECT column,… FROM tb_name WHERE definition
    

WHERE 关键字后面接有效的表达式（definition），该表达式表示被操作的数据记录必须满足的条件。

除 SELECT 外，WHERE 条件关键字可以用于任何 SQL 语法允许的场合，如 UPDATE（更新）、DELETE（删除）等。

例子：

    
    
    SELECT * FROM user WHERE username = 'Jack'
    

该例子指定查询条件为 username 等于 Jack 的数据。

### WHERE 表达式中运算符说明：

参数说明： 运算符 | 说明  
---|---  
= | 等于  
!= | 不等于，某些数据库系统也写作 <>  
> | 大于  
< | 小于  
>= | 大于或等于  
<= | 小于或等于  
BETWEEN … AND … | 介于某个范围之内，例：WHERE age BETWEEN 20 AND 30  
NOT BETWEEN …AND … | 不在某个范围之内  
IN(项1,项2,…) | 在指定项内，例：WHERE city IN('beijing','shanghai')  
NOT IN(项1,项2,…) | 不在指定项内  
LIKE | 搜索匹配，常与模式匹配符配合使用  
NOT LIKE | LIKE的反义  
IS NULL | 空值判断符  
IS NOT NULL | 非空判断符  
NOT、AND、OR | 逻辑运算符，分别表示否、并且、或，用于多个逻辑连接。  
优先级：NOT > AND > OR  
% | 模式匹配符，表示任意字串，例：WHERE username LIKE '%user'  
  
## 一些 WHERE 例子

根据用户名查询指定用户：

    
    
    SELECT * FROM user WHERE username = 'Jack'
    


    

搜索用户名中含有 user 字样的所有用户：

    
    
    SELECT * FROM user WHERE username LIKE '%user%'
    

搜索用户名中含有 user 或者 admin 的所有用户：

    
    
    SELECT * FROM user WHERE username LIKE '%user%' OR username LIKE '%admin%'
    
## 统计数据行数

SELECT COUNT() FROM 语法用于从数据表中统计数据行数。

语法：
    
    
    SELECT COUNT(column) FROM tb_name
    

该 SQL 语法用于统计某一字段的数据行数，COUNT() 内不能是多个字段，但可以是 * 号。

例子：统计用户表数量
    
    
    SELECT COUNT(uid) FROM user";
  
## MySQL LIMIT

MySQL 中 LIMIT 关键字用于限定查询记录返回最大数目。

语法：
```
 ... LIMIT offset , rows
```


该语法中，offset表示偏移量（指向数据记录的游标），rows表示查询限定返回的最大记录数，这两个参数必须为整数。

例子：
```
 SELECT username FROM user LIMIT 4,10
```


如果 user 表中的数据记录超过14条的话，该例子将会返回符合结果的第 5-14 条记录（共 10 条），注意默认偏移量是从 0 开始的。

offset 参数如果省略，则默认为 0 ，即 LIMIT 10 等同于 LIMIT 0,10 （返回符合查询条件的前 10 条记录）。



### 小技巧

当你确认查询结果只有一条数据时（如核对用户名密码），可以加上LIMIT

1的限制条件，当系统查询到一条数据后即停止搜索而不会继续查找下一条记录，这样可有效提高查询效率。
