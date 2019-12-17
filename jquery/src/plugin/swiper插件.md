#  Swiper5 使用方法

1.首先加载插件，需要用到的文件有swiper.min.js和swiper.min.css文件。可下载[Swiper文件](/download/index.html#file1)或使用[CDN](/cdn/index.html)。

    
    
    <!DOCTYPE html>
    <html>
    <head>
        ...
       <link rel="stylesheet" href="https://unpkg.com/swiper/css/swiper.min.css"> 
    </head>
    <body>
        ...
        <script src="https://unpkg.com/swiper/js/swiper.min.js"></script>
        ...
    </body>
    </html>

2.HTML内容。

    
    
    <div class="swiper-container">
        <div class="swiper-wrapper">
            <div class="swiper-slide">Slide 1</div>
            <div class="swiper-slide">Slide 2</div>
            <div class="swiper-slide">Slide 3</div>
        </div>
        <!-- 如果需要分页器 -->
        <div class="swiper-pagination"></div>
        
        <!-- 如果需要导航按钮 -->
        <div class="swiper-button-prev"></div>
        <div class="swiper-button-next"></div>
        
        <!-- 如果需要滚动条 -->
        <div class="swiper-scrollbar"></div>
    </div>
    导航等组件可以放在container之外

3.你可能想要给Swiper定义一个大小，当然不要也行。

    
    
    .swiper-container {
        width: 600px;
        height: 300px;
    }  

4.初始化Swiper：最好是挨着</body>标签

    
    
    ...
    <script>        
      var mySwiper = new Swiper ('.swiper-container', {
        direction: 'vertical', // 垂直切换选项
        loop: true, // 循环模式选项
        
        // 如果需要分页器
        pagination: {
          el: '.swiper-pagination',
        },
        
        // 如果需要前进后退按钮
        navigation: {
          nextEl: '.swiper-button-next',
          prevEl: '.swiper-button-prev',
        },
        
        // 如果需要滚动条
        scrollbar: {
          el: '.swiper-scrollbar',
        },
      })        
      </script>
    </body>

如果不能写在HTML内容的后面，则需要在页面加载完成后再初始化。

    
    
    <script>
    window.onload = function() {
      ...
    }
    </script>

或者这样（Jquery和Zepto）(推荐)

    
    
    <script>
    $(document).ready(function () {
     ...
    })
    </script>

5.完成。恭喜你，现在你的Swiper应该已经能正常切换了。

如果作为CommonJs 或ES 模块引入

    
    
    //CommonJs
    var Swiper = require('swiper');    
    var mySwiper = new Swiper('.swiper-container', { /* ... */ });
    
    //ES
    import Swiper from 'swiper';    
    var mySwiper = new Swiper('.swiper-container', { /* ... */ });