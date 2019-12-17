# PHP $_POST

**$_POST 变量用于接收表单 method="post" 方式发送的表单信息。**

## PHP $_POST

$_POST 变量用于获取由 HTTP POST 方式发送的表单数据。其数据结构是一个关联数组，键名为表单元素的 name ，值为对应的表单取值。

表单 form.html：

    
    
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
    

在 comment.php 中，打印出 $_POST 信息：

    
    
    <?php
    print_r($_POST);
    ?>
    

输出如下：

    
    
    Array
    (
         => 小明
    )
    

## 访问 $_POST 变量

可以像访问普通数组一样方便的访问 $_POST 变量：

    
    
    <?php
    echo '您的称呼是：',$_POST["nickname"]; 
    ?>
    

POST 方法发送的数据对任何人都是不可视的，且对发送信息的量几乎无限制，对于敏感数据（如密码）或者大容量的数据信息提交，通常采用的是 POST 方式。
