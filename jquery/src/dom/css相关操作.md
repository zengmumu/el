# CSS 相关操作

### CSS()方法
~~~
    // 获取元素的css
    $("h1").css("font-size");
    
    // 设置css
    $("h1").css("font-size","14px");
    
    // 设置多个css属性
    $("h1").css({"font-size"："14px","color":"red"});
    
~~~

### 位置
**offset()**
获取匹配元素在当前视口的相对偏移。
返回的对象包含两个整形属性：top 和 left。

**position()**
获取匹配元素相对父元素的偏移。
返回的对象包含两个整形属性：top 和 left。

**scrollLeft()**
获取匹配元素相对滚动条左侧的偏移; scrollLeft(300)
设置元素相对滚动条左边的偏移值


**scrollTop()**
获取匹配元素相对滚动条上边的偏移; scrollTop(300)
设置元素相对滚动条上边的偏移值

### 案例 固定到顶部的导航

html
~~~
<h3>offset 距离</h3>
<div class="banner">banner</div>
<div class="nav">nav</div>
<p>line1</p>
<p>line2</p>
...
<p>line99</p>
<p>line100</p>

~~~

js

~~~
// 思路：只要滚动的距离 大于 元素 nav 距页面顶部的距离  让 nav 固定定位  else   就 默认定位
$(function(){
	var offT=$(".nav").offset().top;
	//nav 距离顶部的距离
	$(window).scroll(function(){
	//窗口发生滚动事件
		var scrollT=$(window).scrollTop();
		//窗口滚动条滚过去的距离
		if(scrollT>offT){
		//如果大于这个距离添加一个固定的class
			$(".nav").addClass("fixed")
			$("body").css("padding-top","50px")
		}else{
			$(".nav").removeClass("fixed")
			$("body").css("padding-top","0")
		}
		
	})
})

~~~

CSS

~~~
.banner{ 
    height:500px ;
    background-color:lightgreen;
}

.nav{ 
    height: 50px; 
    background-color: lightsalmon;
}

.fixed{
    position: fixed;
    top: 0; 
    width: 100%;
    left: 0; 
    z-index: 10;
   /* 注意要写 z-index 不然会被遮盖到下面*/
}



~~~
