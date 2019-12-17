# PHP Session

## PHP Session 概述

session 是一种客户与网站（服务器）更为安全的对话方式。一旦开启了 session
会话，便可以在网站的任何页面使用（保持）这个会话，从而让访问者与网站之间建立了一种“对话”机制。

常见的网上购物车，就是一个session会话的典型应用。我们在预定商品的时候，将选择好的商品放入购物车，实际就是开启一个商品的session会话。如果对选择的商品下了订单，则会将对应信息写入数据库；如果最终没有下订单，在用户关闭浏览器或退出登陆的时候，则会关闭session会话，选择的商品随即失效。

session 会话会为每一个开启了 session 会话的访问者建立一个唯一的会话 ID ，用于识别用户。该会话 ID 可能存储于用户电脑的 cookie
内，也可能通过 URL 来传递。而对应的具体 session 值会存储于服务器端，这也是与 cookie 的主要区别，并且安全性相对较高。

## 创建 session

要创建 session ，必须先使用 session_start() 函数开启一个 session 会话，系统会分配一个会话 ID：

    
    
    <?php
    session_start();
    ?>
    

使用 session_register() 函数注册一个 session 变量，成功返回 TRUE ，否则返回 FALSE 。

语法：

    
    
    bool session_register( mixed name [, mixed ...] )
    

使用 session_register() 函数可以在目前会话下注册一个或多个全局 session 变量。

例子：

    
    
    <?php
    session_start();
    $username = "xiaoli";
    session_register("username");
    ?>
    

在该例子中，我们向 session 注册了一个名为 username 的变量，其值为 xiaoli 。

## 读取 session

PHP 内置的 $_SESSION 变量可以很方便的访问设置的 session 变量。

例子：

    
    
    <?php
    session_start();
    echo "登记的用户名为：".$_SESSION["username"];    //输出 登记的用户名为：xiaoli
    ?>
    

## 销毁 session

可以通过 session_unregister() 函数来注销单个 session 变量或使用 session_unset() 来注销整个 session
会话。

例子：

    
    
    <?php
    session_start();
    session_unregister("username");    //注销 session 变量
    session_unset();                    //注销 session 会话
    ?>
    

## 另一种方式

可以通过直接添加 $_SESSION 数组成员的方式注册 session 变量：

    
    
    <?php
    session_start();
    $_SESSION["username"] = "xiaoli";
    ?>
    

如果要注销这种方式注册的 session 变量，需要使用 unset() 函数：

    
    
    <?php
    session_start();
    unset($_SESSION["username"]);
    ?>
    

读取 session 变量与销毁 session 会话则同前面的方式相同。

### 提示

不可使用 unset() 来销毁 session 会话。
