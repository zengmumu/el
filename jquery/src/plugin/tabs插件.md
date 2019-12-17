# tabs插件
```js
;(function(){
	$.fn.extend({
		"tab":function(opt){
		 
				var DEFAULT={
					"effect":"toggle" ,  		//effect 效果    toggle  | fade |  slide
					"default":0,				//默认显示第几个
					"titleName":".tab_title", 	// 控制器名称  .tab_title
					"contentName":".tab_con",	 // 内容名称  .tab_con
					"speed":"normal"			// 动画的速度   "normal" | "fast" |"slow" | 毫秒
				};
				var option=$.extend({},DEFAULT,opt);
				console.log(option)	
				var dom=$(this);
				//1,控制块
				var titles=dom.find(option.titleName);
				var contents=dom.find(option.contentName);
				console.log(titles);
				if(option.default<0){option.default=0}
				if(option.default>=contents.length){option.default=contents.length-1}
				
				init();
				
				function init(){
					$(titles[option.default]).addClass("active");
					contents.hide();
					$(contents[option.default]).show();
				}
				//titles 单击对应的 contents 显示
				titles.bind("click",change);
				function change(){
					var behide = dom.find(option.contentName+":visible");
					var num=titles.index($(this));//找出是第几个被单击
					dom.find(".active").removeClass("active");
					$(this).addClass("active");
					if(option.effect=="toggle"){
						behide.hide();
					$(contents[num]).show();
					}else if(option.effect=="fade"){
						behide.fadeOut(option.speed);
						$(contents[num]).fadeIn(option.speed);
					}else if(option.effect=="slide"){
						behide.slideUp(option.speed);
						$(contents[num]).slideDown(option.speed);
					}
				}
				
				
			 
		}
		
	})
	
	
})($)
```

# 插件调用
```
<!DOCTYPE html>
<html lang="cn">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<script src="http://libs.baidu.com/jquery/2.0.0/jquery.min.js"></script>
	<script src="tab.js"></script>
	<style>
		 .active{color:orange;}
		 .tabs .tab_title{ 
		 	float: left; 
		 	line-height: 30px; 
		 	border:1px solid #f0f0f0; 
		 	margin-left: -1px;
		 	padding: 0 15px;
		 }
		 .tabs .tab_con{ background: #fafafa; clear: both; }
	</style>
</head>
<body>
	<div class="tabs">
		<div class="tab_title">标题1</div> <div class="tab_title">标题2</div> <div class="tab_title">标题3</div>
		<div class="tab_con">内容1</div>
		<div class="tab_con">内容2</div>
		<div class="tab_con">内容3</div>
	</div>
	<div class="tabs2">
		<div class="title">标题1</div> <div class="title">标题2</div> <div class="title">标题3</div>  <div class="title">标题4</div>
		<div class="con">内容1</div>
		<div class="con">内容2</div>
		<div class="con">内容3</div>
		<div class="con">内容4</div>
	</div>
	<div class="tabs3">
		<ul>
			<li>标题1</li> <li>标题2</li> <li>标题3</li> <li>标题4</li>	
		</ul>
		
		<div class="con">内容1</div>
		<div class="con">内容2</div>
		<div class="con">内容3</div>
		<div class="con">内容4</div>
	</div>

	 <script>
	 	$(function(){
	 			$(".tabs").tab({default:2,effect:'slide',speed:3000,})
	 			$(".tabs2").tab({titleName:'.title',contentName:'.con'})
	 			$(".tabs3").tab({titleName:'li',contentName:'.con'})
	 	})
	 	
	 </script>
</body>
</html>
```