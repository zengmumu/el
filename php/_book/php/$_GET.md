# PHP $_GET

**$_GET 变量用于接收表单 method="get" 方式发送的表单信息。**

## PHP $_GET

$_GET 变量的数据结构同 $_POST 类似，也是一个关联数组，键名为表单元素的 name，用于收集以 HTTP GET 方式请求的数据。

表单 form.html：

    
    
    <html>
    <body>
    <form name="commentform" method="get" action="comment.php">
    <p>
    称呼: <input type="text" name="nickname" />
    </p>
    <input type="submit" value="提 交" />
    </form>
    </body>
    </html>
    

将前面的例子表单改为 GET 方式，输入称呼后，在浏览器地址栏，看起来类似如下（IE 浏览器下中文可能会经 encode 编码）：

    
    
    http://www.5idev.com/html/comment.php?nickname=%D0%A1%C3%F7
    

取得 GET 表单数据：

    
    
    <?php
    echo '您的称呼是：',$_GET["nickname"]; 		//输出：您的称呼是：小明
    ?>
    

### 提示

  1. GET 方式会把表单数据暴露在浏览器地址栏里，因此不宜发送敏感数据（如密码等），敏感信息发送请使用 POST 方式。
  2. GET 方式对发送的信息量有一定限制，如果发送较大的信息，请使用POST 方式。
  3. GET 方式访问的页面可以加入收藏夹而在以后可以直接访问，而 POST 方式访问的页面则不能。

## HTTP GET

HTTP GET 方式不仅是用于表单数据发送，它是指更广泛的以实体的方式得到由请求 URL （浏览器地址）所指定资源的信息。具体参见《[XHTML
Get与Post](p-xhtml_get_post.shtml)》。

利用 HTTP GET 方式还可以向网页传递数据信息，如下面这个地址：

    
    
    http://www.5idev.com/html/article.php?id=10
    

在该例子中，就通过地址 GET 方式向 article.php 传递了一个 id=10 的信息。在 article.php 中可以通过
$_GET["id"] 取得数据，其实际作用可能是从数据库中读取 id 为 10 的这篇文章，多个数据以 & 符号来连接：

    
    
    http://www.5idev.com/html/article.php?type=2&id=10
    

article.php 中取得 GET 数据：

    
    
    <?php
    echo $_GET["type"];		//输出 2
    echo $_GET["id "];		//输出 10
    ?>
    

## PHP $_REQUEST

在 PHP 中还预定义了 $_REQUEST 变量，它包含了 $_POST 、$_GET 、和 $_COOKIE 。其访问方式同 $_POST 等：

    
    
    <?php
    echo $_REQUEST["nickname"]	//输出用户输入的称呼
    echo $_REQUEST["id "];		//输出 10
    ?>
    
