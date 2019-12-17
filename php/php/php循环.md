# PHP while 循环

**PHP 循环控制主要是 while 循环和 for 循环。**

## while循环

while循环是PHP中最简单的循环，其基本格式为：

    
    
    while (expr){
        statement
    }
    //或者
    while (expr):
        statement
    endwhile;
    

该语法表示，只要expr表达式为TRUE，那么就一直执行statement直到expr为FALSE为止，statement表示要执行的动作或逻辑。

例子：

    
    
    <?php
    $i = 1;
    while ($i <= 10) {
       echo $i;
       $i++;
    }
    ?>
    

该例子循环输出1到10。

# PHP for 循环

## for循环

for循环是PHP中更为复杂的循环，其语法如下：

    
    
    for (expr1; expr2; expr3){
        statement
    }
    

下面的例子依然输出1到10：

    
    
    <?php
    for ($i = 1; $i <= 10; $i++) {
        echo $i;
    }
    ?>
    

### 语法解读

  1. 第一个表达式（expr1）在循环开始前无条件求值一次
  2. expr2 在每次循环开始前求值，如果值为 TRUE，则继续循环，执行嵌套的循环语句；如果值为 FALSE，则终止循环。
  3. expr3 在每次循环之后被求值（执行）
  4. 每个表达式都可以为空。如果expr2 为空意则将无限循环下去，但可以通过break来结束循环：
    
        <?php
    for ($i = 1; ; $i++) {
        if ($i > 10) {
            break;
        }
        echo $i;
    }
    ?>
    

### 提示

在使用循环语句的时候，我们通常要注意不要无限循环而造成程序“僵死”，另外还要注意循环条件（循环判断表达式），以确保循环结果正确。