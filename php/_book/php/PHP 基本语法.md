# PHP 基本语法

## PHP 书写格式

从一个例子开始。

启动编辑器，创建一个php文件并键入如下代码：

    
    
    <?php
    echo "你好！";
    ?>
    

将该文件命名为 test.php 并存储于 D:\phpStudy\PHPTutorial\WWW 目录下。
`前提是phpstudy默认安装在d盘`  
在浏览器地址栏里访问该 php 文件：http://127.0.0.1/test.php，输出结果如下：

    
    
    你好！
    

我们通过浏览器查看网页的源代码，也只是：

    
    
    你好！
    

在该例子中，我们以 echo 指令输出一个字符串“你好！”。

从这个例子可以看出：

  1. PHP 文件或 PHP 代码段以“<?php”开头，以“?>”结束，中间为php代码
  2. 每一个指令集以 ; 符号结束
  3. 浏览器得到的为 PHP 解析器执行完 php 代码后的结果，网站浏览者不能查看到 php 文件的原始代码

当然，要输出标准的html代码，可以把上例完善为：
```php    
    <html>
     <head>
      <title>PHP 测试</title>
     </head>
     <body>
     <p>
    <?php
    echo "你好！";
    ?>
     </p>
     </body>
    </html>
```    

可见，PHP 代码可以和 XHTML 代码混写。

echo 是 PHP 内置的一个指令，用于输出1个或多个字符串，和 echo 类似的还有 print。

