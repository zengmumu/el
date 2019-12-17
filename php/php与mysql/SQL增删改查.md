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


