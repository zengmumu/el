# MySQL mysql_query 函数执行SQL语句

## mysql_query()函数

PHP MySQL 函数库中，mysql_query() 函数用于向 MySQL 发送并执行 SQL 语句。

对于没有数据返回结果集的 SQL ，如 UPDATE、DELETE 等在执行成功时返回 TRUE，出错时返回 FALSE；对于
SELECT，SHOW，EXPLAIN 或 DESCRIBE 语句返回一个资源标识符，如果查询执行不正确则返回 FALSE。

语法：

    
    
    resource mysql_query( string query [, resource connection] )
    

参数说明： 参数 | 说明  
---|---  
query | 要发送查询的 SQL 语句  
connection | 可选，连接数据库标识资源，如果不指定则使用上一连接  
  
### 提示

  1. 如果没有打开的连接，本函数会尝试无参数调用 mysql_connect() 函数来建立一个连接
  2. 对于返回数据集的查询，就算返回结果为0（即没有符合查询条件的记录），返回的仍然是资源标示符而不是 FALSE 

例子1：

    
    
    <php
    $conn = @mysql_connect("localhost","root","root123");
    if (!$conn){
    	die("连接数据库失败：" . mysql_error());
    }
    mysql_select_db("test", $conn);
    $result = mysql_query("SELECT * WHERE 1=1")
        or die("无效查询: " . mysql_error());
    ?> 
    

该例子查询语句在 SQL 语法上有错误，因此 mysql_query() 执行失败并返回 FALSE 。

例子2：

    
    
    <php
    $conn = @mysql_connect("localhost","root","root123");
    if (!$conn){
        die("连接数据库失败：" . mysql_error());
    }
    
    mysql_select_db("test", $conn);
  
    $password = md5("123456");		//原始密码 12345 经过加密后得到加密后密码
    $regdate = time();			//得到时间戳
    $sql = "INSERT INTO user(username, password, email, regdate)VALUES('小王', '$password',
     '12345@163.com', $regdate)";
    
    if(!mysql_query($sql,$conn)){
        echo "添加数据失败：".mysql_error();
    } else {
        echo "添加数据成功！";
    }
    ?> 
    

该例子向 user 表写入数据，成功返回 TRUE ，否则返回 FALSE（用 ! 符号判断）。
