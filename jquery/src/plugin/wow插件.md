# WOW.js – 让页面滚动更有趣

分类：[代码](http://www.dowebok.com/code) 日期：2016-08-22 点击(342,517)
评论([33](http://www.dowebok.com/131.html#comments))

![WOW.js - 让页面滚动更有趣](http://img1.dowebok.com/131.jpg)

[演示1](http://www.dowebok.com/demo/131/ "演示1")
[演示2-仿oppo首页](http://www.dowebok.com/demo/131/index2.html "演示2-仿oppo首页")
[下载](http://www.400gb.com/file/73017626 "下载")

## 简介

有的页面在向下滚动的时候，有些元素会产生细小的动画效果。虽然动画比较小，但却能吸引你的注意。比如刚刚发布的 iPhone 6
的页面（查看）。如果你希望你的页面也更加有趣，那么你可以试试 WOW.js。

WOW.js 依赖 [animate.css](http://www.dowebok.com/98.html "animate.css –
齐全的CSS3动画库")，所以它支持 animate.css 多达 60 多种的动画效果，能满足您的各种需求 [animate官网](https://daneden.github.io/animate.css/)



## 使用方法

### 1、引入文件

    
    
    <link rel="stylesheet" href="http://biger.applinzi.com/api/css/animate.min.css">
    <script src="http://biger.applinzi.com/api/js/wow.min.js"></script>
### 2、HTML

    
    
    <div class="wow slideInLeft"></div>
    <div class="wow slideInRight"></div>

可以加入 data-wow-duration（动画持续时间）和 data-wow-delay（动画延迟时间）属性，如：

    
    
    <div class="wow slideInLeft" data-wow-duration="2s" data-wow-delay="5s"></div>
    <div class="wow slideInRight" data-wow-offset="10"  data-wow-iteration="10"></div>

### 3、JavaScript

    
    
    new WOW().init();

如果需要自定义配置，可如下使用：

    
    
    var wow = new WOW({
        boxClass: 'wow',
        animateClass: 'animated',
        offset: 0,
        mobile: true,
        live: true
    });
    wow.init();

## 配置

属性/方法 | 类型 | 默认值 | 说明  
---|---|---|---  
boxClass | 字符串 | ‘wow’ | 需要执行动画的元素的 class  
animateClass | 字符串 | ‘animated’ | animation.css 动画的 class  
offset | 整数 | 0 | 距离可视区域多少开始执行动画  
mobile | 布尔值 | true | 是否在移动设备上执行动画  
live | 布尔值 | true | 异步加载的内容是否有效  
  
[演示1](http://www.dowebok.com/demo/131/ "演示1")
[演示2-仿oppo首页](http://www.dowebok.com/demo/131/index2.html "演示2-仿oppo首页")
[下载](http://www.400gb.com/file/73017626 "下载")

标签：[animate.css](http://www.dowebok.com/tag/animate-
css)[滚动](http://www.dowebok.com/tag/scroll)
