 



## lightbox

  1. 下载 [Github ](https://github.com/lokesh/lightbox2/releases).  


  2. 导入css jQuery light.box
  ```
  <link rel="stylesheet" href="http://biger.applinzi.com/api/css/lightbox.css">
  <script src="http://biger.applinzi.com/api/js/jquery-1.11.0.min.js"></script>
  <script src="http://biger.applinzi.com/api/js/lightbox.min.js"></script>
  ```

 3. 初始化html  
**单张图片**。将data-lightbox属性添加到任何图像链接以启用灯箱。对于属性的值，请为每个图像使用唯一的名称。例如：
```
<a href="images/image-1.jpg" data-lightbox="image-1" data-title="My caption">Image #1</a>
```
可选参数
* data-title如果要显示标题，请添加属性。
* data-alt如果要设置链接图像的alt属性，请添加一个属性。

**图像集**。如果您有一组要合并为一组的相关图像，请data-lightbox对所有图像使用相同的属性值。例如：
```
<a href="images/image-2.jpg" data-lightbox="roadtrip">Image #2</a>
<a href="images/image-3.jpg" data-lightbox="roadtrip">Image #3</a>
<a href="images/image-4.jpg" data-lightbox="roadtrip">Image #4</a>
```
案例
```
<p>
	<a href="img/demopage/image-1.jpg" data-lightbox="g">
	    <img src="img/demopage/thumb-1.jpg" alt="">
	</a>
</p>

<p><a href="img/demopage/image-3.jpg" data-lightbox="groud" title="图片3"><img src="img/demopage/thumb-3.jpg" alt=""></a></p>
<p><a href="img/demopage/image-4.jpg" data-lightbox="groud" title="图片3"><img src="img/demopage/thumb-4.jpg" alt=""></a></p>
<p><a href="img/demopage/image-5.jpg" data-lightbox="groud" title="图片3"><img src="img/demopage/thumb-5.jpg" alt=""></a></p>
```

 



## 参数
如果要更改任何默认选项，请调用option方法。
```
<script>
    lightbox.option({
      'resizeDuration': 200,
      'wrapAround': true
    })
</script>
```
选项 | 默认 | 描述  
---|---|---  
alwaysShowNavOnTouchDevices | false |如果为true，则在支持触摸的设备上始终会在查看图像集时在鼠标悬停时显示在鼠标悬停时的左右导航箭头。  
albumLabel | "Image %1 of %2" | 查看图像集时在标题下方显示的文本。默认文本显示当前图像编号和该集中的图像总数。  
disableScrolling | false | 如果为true，请在打开Lightbox时阻止页面滚动。这通过隐藏在身体上的设置溢出起作用。  
fadeDuration | 600 | 灯箱容器和叠加层淡入和淡出所花费的时间（以毫秒为单位）。  
fitImagesInViewport | true |如果为true，则调整将在视口之外延伸的图像的大小，以使其整齐地适合视口。这使用户不必滚动查看整个图像。  
imageFadeDuration | 600 | 加载后图像淡入所需的时间（以毫秒为单位）。  
maxWidth |   | 如果设置，则图像宽度将限于此数字（以像素为单位）。长宽比将无法保持。  
maxHeight |   | 如果设置，则图像高度将限于此数字（以像素为单位）。长宽比将无法保持。  
positionFromTop | 50 | 灯箱容器将出现的距视口顶部的距离，以像素为单位。  
resizeDuration | 700 | 在不同尺寸的图像之间进行过渡时，灯箱容器为其宽度和高度设置动画所需的时间（以毫秒为单位）。  
showImageNumberLabel | true | 如果为false，则将隐藏表示当前图像编号和已设置图像总数（例如"image 2 of 4"）的文本。  
wrapAround | false |如果为true，则当用户到达集合中的最后一张图像时，将显示向右导航箭头，他们将继续向前移动，这会将他们带回到集合中的第一张图像。

