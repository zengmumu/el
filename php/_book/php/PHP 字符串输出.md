
## PHP 字符串输出

用于字符串输出的函数主要有：

  * echo()：输出一个或多个字符串
  * print()：输出一个字符串
  * printf()：输出格式化字符串

## echo()

echo()是指令而不是函数，它没有返回值，可以输出一个或多个字符串。

语法：

    
    
    void echo ( string arg1 [, string ...] )
    

例子：

    
    
    <?php
    $foo = "foobar";
    $bar = "barbaz";
    echo $foo,$bar;		// 输出"foobarbarbaz"
    echo "<br />";
    echo $foo[3];		// 输出第4个字符"b"
    echo "<br />";
    echo "foo is $foo";	// 输出"foo is foobar"
    echo "<br />";
    echo 'foo is $foo';	// 输出"foo is $foo"
    ?>
    

### 说明

  * 双引号内的变量会被解释，而单引号内的变量则原样输出
  * 字符串计算是从 0 开始计数

## print()

print() 用于输出一个字符串。print() 是函数，返回一个整型，但只能有一个参数，其用法同 echo ，但不能输出数组和对象。

语法：

    
    
    int print( string arg )
    

## printf()

printf() 用于格式化输出字符串，返回一个整型。

语法：

    
    
    int printf(string format, arg1, arg2,  ...)
    

format 为字符串以及变量的格式化方式，arg1 为插入第一个%符号处的参数，agr2等以此类推。

格式化方式说明： 格式化方式 | 说明  
---|---  
%d | 十进制有符号整数  
%u | 十进制无符号整数  
%f | 浮点数  
%s | 字符串  
%c | 单个字符  
%p | 指针的值  
%e | 指数形式的浮点数  
%x/%X | 无符号以小/大写十六进制表示的整数  
%o | 无符号以八进制表示的整数  
%g | 自动选择合适的表示法  
  
例子：

    
    
    <?php
    $str = "This";
    $number = 31;
    printf("%s month has %u days",$str,$number);    //输出 This month has 31 days
    ?>
    
