# $符号-jquery与js相互转换
作者：曾庆林
### 获取Dom对象
**JavaScript方式**
~~~
var id=document.getElementById("id");
~~~
**jQuery方式**
~~~
var $id=$("#id");
~~~

### js Dom对象 转换为jQuery 对象
`$(expression)`
接收一个包含 CSS 选择器的字符串，然后用这个字符串去匹配一组元素

将一个或多个DOM元素转化为jQuery对象  注意是jQuery对象，而不是DOM对象
~~~
var myh=document.getElementsByTagName("h1")[2];
$(myh).css("color","red"); 
// 转换为jquery对象才能用jQuery的方法
~~~

jQuery 的核心功能都是通过这个函数实现的

### jQuery转换成js对象
只需在jQuery对象后跟一个索引值（如[0]）—因为它得到的是一个对象数组，即可得到DOM对象。然后就可以使用innerHTML、innerText等DHTML方法和属性了。
~~~
$("h1").css("color","red");
alert($("h1")[0].innerHTML); 
// 得到数组中的第一个DOM对象
~~~

另外也可以用
~~~
var id=$id.get(0);
~~~