# MySQL mysql_fetch_array 

 

从查询返回的结果集中取得相关的查询结果

  
  * mysql_fetch_assoc()：从结果集中取得一行作为关联数组
 


例子  ，使用 MYSQL_ ASSOC ：

    
    
    $conn = @mysql_connect("localhost","root","root123");
    if (!$conn){
        die("连接数据库失败：" . mysql_error());
    }
    
    mysql_select_db("test", $conn);
    $result = mysql_query("SELECT uid,username FROM user");
    while($row = mysql_fetch_array_assocc($result)){
        echo "用户ID：".$row['uid']."<br />";
        echo "用户名：".$row['username']."<br />";
    }
    

浏览器输出：
    
    用户ID：1
    用户名：admin
    用户ID：2
    用户名：小明
    用户ID：3
    用户名：Jack
    用户ID：4
    用户名：小王
    

 


