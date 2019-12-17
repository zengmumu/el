# jqzoom
 第一步导入css
 ```
<script src="http://biger.applinzi.com/api/js/jquery-3.3.1.js"></script>
<script src="http://biger.applinzi.com/api/js/jquery.jqzoom.js"></script>
<link rel="stylesheet" href="css/jqzoom.css">
<style>
	.jqzoom{float: left;}
</style>
 ```
 # 初始化
 ```
 	<script>
		$(function(){
			$(".jqzoom").jqueryzoom({
				xzoom:500, //放大图的宽度(默认是 200)
				yzoom:500,	//放大图的高度(默认是 200)
				offset:0,	//离原图的距离(默认是 10)
				position:"right",  //放大图的定位(默认是 right)
				preload:1

			});
		})
	</script>
 ```
 ### html解构
 ```
 div class="jqzoom">
		<img src="images/thumb-1.jpg" jqimg=" images/image-1.jpg" alt="">
	</div>
 ```