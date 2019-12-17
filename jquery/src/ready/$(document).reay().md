### 页面载入
作者：曾庆林

window.onload方法长久以来是程序员解决客户端页面载入问题的一个方法，只有少数大型的图片文件会被快速的载入，而大部分大型的图片文件会使window.onload()载入的很慢.

**DOM 1.0 加载方式**
~~~
window.onload=init;
function init(){
	alert("abc");
}
window.onload=init2;
function init2(){
	alert("123");
}
~~~
>多次使用后面的方法会覆盖前面的方法
**DOM 2.0 加载方式（W3C）**
~~~
window.addEventListener("load",init,false);
function init(){
	alert("abc")
}
window.addEventListener("load",init2,false);
function init2(){
	alert(123);
}
~~~
>不兼容早期的ie浏览器

**ie早期版本 加载方式**
~~~
window.attachEvent("onload",init);
window.attachEvent("onload",init2);
function init(){
	alert("abc")
}
function init2(){
	alert(123);
}
~~~

**兼容方式写法**
~~~
function addEvent(elem,type,fn){
	if(elem.addEventListener){
		elem.addEventListener(type,fn,false);
	}else if(elem.attachEvent){
		elem.attachEvent("on"+type,fn);
	}
}
		
addEvent(window,"load",init1);	
addEvent(window,"load",init2);

function init1(){
	alert("abc")
}

function init2(){
	alert(123);
}
~~~

**jQuery 页面加载写法**
~~~
$(document).ready(function() {

});
~~~

简写
~~~
$(function(){

});
~~~

**总结**



标题 | window.onload | $(document).ready()
---|---|---
执行时机 | 必须等待网页全部加载完毕（包括 图片等），然后再执行包裹代码 | 只需要等待网页中的DOM结构 加载完毕，就能执行包裹的代码
执行次数 | 只能执行一次，如果第二次，那么 第一次的执行会被覆盖 | 可以执行多次，第N次都不会被上 一次覆盖




