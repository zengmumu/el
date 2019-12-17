# Class 操作
作者：曾庆林

### 设置和切换class
addClass() 添加class
```
$(elem).addClass("active");
//注意class active 前面没有加点
    
```

hasClass() 检查是否有某个class名 返回true/false

removeClass() 删除class
```
<h1 class="active header"></h1>
<script>
$(function({
     $("h1").removeClass("active");
    // 这样只会删除 active class
    
    $("h1").removeClass();
    // 这样会删除掉h1的所有class
   
}))
</script>
    
```


toggleClass() 切换class

example：单击添加切换高亮显示

```

<style>
    .active{ color:red;}
</style>

<h1 class="active header"></h1>

<script>
$(function({
    $("h1").click(function(){
         $("h1").toggleClass("active");
     })
    
}))
</script>
    
```

