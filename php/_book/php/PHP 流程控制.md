
# 流程控制
## if

if 流程控制允许按照条件执行代码片段。if 流程控制分为三类：

  1. if
  2. if…else
  3. elseif

### if

语法：

    
    
    if (expr){
        statement
    }
    

例子：

    
    
    <?php
    if ($x > $y)
        echo "x 大于 y";
    ?>
    

### if…else

语法：

    
    
    if (expr){
        statement1
    } else {
        statement2
    }
    

它表示只要 expr 成立，则执行 statement1 ，否则执行 statement2 。

例子：

    
    
    <?php
    if ($x > $y)
        echo "x 大于 y";
    } else {
        echo "x 小于等于 y";
    }
    ?>
    

### elseif

语法：

    
    
    if (expr){
        statement1
    } elseif (expr2) {
        statement2
    } else {
        statement3
    }
    

它表示只要 expr1 成立，则执行 statement1 ，否则检测 expr2 ，如果 expr2 成立则执行 statement2 。如果 expr2
也不成立，则执行 statement3 。

例子：

    
    
    <?php
    if ($x > $y) {
        echo "x 大于 y";
    } elseif ($x == $x) {
        echo "x 等于 y";
    } else {
        echo "x 小于 y";
    }
    ?>
    

### 提示

elseif 可以有多个，以实现更多条件的选择，但多数情况下，条件更多时，我们可以选择switch来实现。