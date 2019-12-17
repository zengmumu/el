# PHP 表单

**PHP 预定义了 $_POST 和 $_GET 变量来接收表单信息。**

## HTML 表单

表单例子，form.html：

    
    
    <html>
    <body>
    <form name="commentform" method="post" action="comment.php">
    <p>
    称呼: <input type="text" name="nickname" />
    </p>
    <input type="submit" value="提 交" />
    </form>
    </body>
    </html>
    

上面的例子中，表单信息包含了一个（称呼）输入框和 提交 按钮。当点击 提交 按钮时，网页就会把表单信息（用户输入的称呼）以 POST 方式提交给
comment.php 文件处理。

comment.php 文件：

    
    
    <html>
    <body>
    <p>您的称呼是：<?php echo $_POST["nickname"]; ?></p>
    </body>
    </html>
    

当我们在 form.html 输入框里输出称呼：小明，点击 提交 按钮，comment.php 页面显示：

    
    
    您的称呼是：小明
    

上面就是一个简单的表单处理过程，PHP 预定义了 $_POST 和 $_GET 变量来接收表单信息，请参看《[PHP
$_POST](p-php_post.shtml)》与《[PHP $_GET](p-php_get.shtml)》

## HTML 表单验证

表单用于收集客户的输入信息时，不要想当然的以为客户会按照设想中的输入符合规定的内容。任何时刻都要对客户的输入做严格检查。

### 客户端验证

客户端表单验证一般是基于 Javascript 脚本的验证方式，这种验证方式能有效减少服务器的负担，也能即时提醒客户输入的错误之处。客户端
Javascript 表单验证例子可参看 [PHP实践教程](php-practice.shtml) 之《[PHP
用户注册](p-php_user_reg.shtml)》验证内容。

### 服务器端验证

在某些情况下，除了进行客户端的验证外，可能还需要进行服务器端的验证（如访问数据库）。这时候需要在 PHP
程序里做好逻辑上的验证。关于服务器端验证