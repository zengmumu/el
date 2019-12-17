# [lazyload.js详解](http://www.cnblogs.com/yzg1/p/5051554.html)

## 简介

lazyload.js用于长页面图片的延迟加载，视口外的图片会在窗口滚动到它的位置时再进行加载，这是与预加载相反的。

## 优点：

  * 它可以提高页面加载速度；
  * 在某些情况清晰它也可以帮助减少服务器负载。



## 使用

lazyload依赖与jquery。所以先引入jquery和lazyload

    
    
   <script src="http://libs.baidu.com/jquery/2.0.0/jquery.min.js"></script>
    <script src="biger.applinzi.com/api/js/jquery.lazyload.min.js"></script>

1.将图片路径写入data-original属性  
2.给lazyload的图片增加一个名为lazy的class  
3.选择所有要lazyload的图片（img.lazy），执行lazyload();

    
    
    <img class="lazy" data-original="img/example.jpg" style="margin-top:1000px" height="200">
    <script>
        $(function(){
            $("img.lazy").lazyload();
        })
    </script>

注意：必须设置图片的高度或者宽度，否则插件可能无法正常工作

# 背景图懒加载
大多数人使用[Lazy Load Plugin for
jQuery](http://www.appelsiini.net/projects/lazyload)，是用于image加载，但其实它还有一个很重要的功能，就是背景图延迟加载。背景图延迟加载的用法和图片延时加载的用法很相似，首先，你需要使用背景的元素需要这样写：

    
    
    <div class="lazy" data-original="img/example.jpg" 
     ></div>

然后用一段js

    
    
    $(function() {
        $("div.lazy").lazyload();
    });

这样，只有当这个div出现在可视视窗内时，背景图才会加载显示。

## 提前加载——Threshold

lazyload默认是当滚动到该图片位置时，加载该图片。但是可以通过设置Threshold参数来实现滚到距离其xx px时就加载。

    
    
        $(function(){
            $("img.lazy").lazyload({
                threshold :20
            });
        })

上面的例子设置了滚动到距离图片20px时，图片就开始再开始加载

## 事件触发(可以是jquery事件，也可以是自定义事件)——Event

当触发定义的事件时，图片才开始加载

    
    
        $(function(){
            $("img.lazy").lazyload({
                event : "click"
            });
        })

上面的例子使图片点击后，才开始加载

Tip:你可以使用这个来实现图片的延迟加载

    
    
    $(function() {
        $("img.lazy").lazyload({
            event : "sporty"
        });
    });
    
    $(window).bind("load", function() {
        var timeout = setTimeout(function() {
            $("img.lazy").trigger("sporty")
        }, 5000);
    });

上面的代码在页面加载完毕后五秒才开始加载图片

## 设定效果——Effects

插件默认的加载效果是 `show()` ,你可以使用任何你想要的效果。下面的代码使用了 `fadeIn()`

    
    
    $("img.lazy").lazyload({
        effect : "fadeIn"
    });

## 滚动容器内的图片——container

插件也可以使用在滚动容器内的图片上。下面的div拥有scrollerbar，内容的内容进行滚动，滚到图片位置时，图片开始加载

    
    
    <div style="height:600px;overflow:scroll" id="container">
        <img class="lazy" data-original="img/example.jpg"  alt="" style="margin-top:1000px" height="200">
    </div>
    <script>
        $(function(){
            $("img.lazy").lazyload({
                container: $("#container")
            });
        })
    </script>

## 不顺序排列的图片

  * 插件会执行一个寻找未加载图片的循坏，该循环会检查图片是否可见，默认情况下，当第一个视图外的图片被找到，循环就会停止 。
  * 但是存在一种情况：页面布局图片的顺序和html图片代码的顺序不一致;它会导致本该加载的没有加载。这种情况下就可以将 failurelimit 设为 10 ，它令插件找到 10 个不在可见区域的图片是才停止搜索. 如果你有一个恶心的布局, 请把这个参数设高一点。

代码：

    
    
    $("img.lazy").lazyload({
        failure_limit : 10
    });

## 处理隐藏图片——skip_invisible

为了提升性能，插件默认忽略隐藏的图片；如果想要加载隐藏图片.设置skip_invisible为false;

注意：Webkit浏览器将自动把没有宽度和高度的图像视为不可见

    
    
    $("img.lazy").lazyload({
        skip_invisible : true
    });  
      
      
      
    
    
    
    转载自<https://www.cnblogs.com/yzg1/p/5051554.html>
    
    
      
      
    Python入门教程通过简短的课程和有趣的小测验进行学习冲浪，展示你的it编程技能。包含html、js、vue、java、php、web前端教程
