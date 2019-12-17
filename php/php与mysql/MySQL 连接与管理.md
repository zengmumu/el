# MySQL 连接与管理

## 让 PHP 支持 MySQL

PHP 有专有的 MySQL 函数库以使用操作 MYSQL 数据库。

在 PHP 5 及以后版本中不再默认支持 MySQL ，所以在运行这些库之前，请确定 php.ini 加载了 MySQL 数据库支持：

    
    
    extension = mysql.dll
    

## MySQL 连接

mysql_connect() 函数用于开启一个到 MySQL 数据库的连接。

语法：

    
    
    mysql_connect( servername, username, password )
    

以上 3 个参数虽然都是可选，但通常情况下我们都需要明确写明。

测试数据库连接的例子：

    
    
    <?php
    $conn = @mysql_connect("localhost","root","root1234");
    if (!$conn){
        die("连接数据库失败：" . mysql_error());
    } else {
        echo "连接数据库成功！";
    }
    ?>
    

在本例子中，用 @ 运算符屏蔽了 mysql_connect() 函数连接失败时的错误提示，改为自定义的错误信息提示。如果连接数据库失败，提示错误提示如下：

    
    
    连接数据库失败：Access denied for user 'root'@'localhost' (using password: YES)
    

在 PHP 程序执行完之后，会自动关闭对数据库的连接。如果想在执行完之前就关闭数据库连接，可以使用 mysql_close() 函数：

    
    
    mysql_close( $conn );
    

请注意其中的参数是对应的连接资源变量。

## 管理 MySQL 数据库

对于 MySQL 的管理，通常是通过 phpMyAdmin 来进行的。关于 phpMyAdmin 的安装，请参见《[phpMyAdmin
安装](p-phpmyadmin_install.shtml "phpMyAdmin 安装")》。

登陆 phpMyAdmin 后，可以做账号权限内允许的各种管理操作。phpMyAdmin 采用 [HTML
框架](p-xhtml_frameset.shtml "点击了解 XHTML 框架")结构，左侧是库表选择，右侧是操作主界面。

![phpmyadmin主界面](/Public/Images/article/php_phpmyadmin_1.gif)

右侧操作主界面上，可以对数据库表进行“浏览数据”、“结构修改”、“运行 SQL
语句”、“搜索”、“插入数据”、“导出”、“导入”、“表属性更改”、“清空”甚至“删除”等操作。不同版本界面及操作上会有些细微差异。

在管理数据库之前，需要对一些基本的概念如创建库、权限、表及表属性以及数据类型等有所了解。要了解这些知识请继续学习后续的教程。

### 提示

通常提供数据库支持的主机商，也会提供 phpMyAdmin 以方便用户管理自己的数据库。
