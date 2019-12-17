## JQuery概述

作者：曾庆林

jQuery由美国人John Resig于2006年初创建，至今已吸引了来自世界各地的众多javascript高手加入其team。
 
 jQuery是一个快速的，简洁的javaScript库，使用户能更方便地处理HTML documents、events、实现动画效果，并且方便地为网站提供AJAX交互。
 
 jQuery能够使用户的html页保持代码和html内容分离，也就是说，不用再在html里面插入一堆js来调用命令了，只需定义id即可。
 
 jQuery是一个优秀的JavaScript库,它凭借简洁的语法和跨平台的兼容性,极大地简化了JavaScript开发人员遍历HTML文档,操作DOM、处理事件、执行动画和开发Ajax的操作。

2006 年 8 月发布了 jQuery1.0，第一个稳定版本，具有对 CSS 选择符、事件处理和 Ajax 交互的支持
j现在最新的版本是jQuery3.0

## jQuery 优点
能够使程序员从设计和书写繁杂的JS应用中解脱出来，将关注点转向功能需求而非实现细节上，从而提高项目的开发速度。

1. 像 CSS 那样访问和操作 DOM 
1. 修改 CSS 控制页面外观 
1. 简化 JavaScript 代码操作
1. 事件处理更加容易 
1. 各种动画效果使用方便 
6. 让 Ajax 技术更加完美 
7. 基于 jQuery 大量插件
8. 自行扩展功能插件

jQuery 最大的优势，就是特别的方便。比如模仿 CSS 获取 DOM，比原生的 JavaScript 要方便太多。并且在多个 CSS 设置上的集中处理非常舒服，而最常用的 CSS 功能又封装到 单独的方法，感觉非常有心 `最重要的是` jQuery 的代码兼容性非常好，你不需要总是头疼 着考虑不同浏览器的兼容问题。

`jQuery2.0以上的版本不兼容IE8`

### 主流的JavaScript框架
- **Angular**  诞生于2009年，由Misko Hevery 等人创建，后为Google所收购。是一款优秀的前端JS框架，已经被用于Google的多款产品当中。AngularJS有着诸多特性，最为核心的是：MVC、模块化、自动化双向数据绑定、语义化标签、依赖注入等等。
- **React** React 起源于 Facebook 的内部项目，因为该公司对市场上所有 JavaScript MVC 框架，都不满意，就决定自己写一套，用来架设Instagram 的网站。做出来以后，发现这套东西很好用，就在2013年5月开源了
- **Vue** 作者（尤雨溪） 是一套构建用户界面的渐进式框架。与其他重量级框架不同的是，Vue 采用自底向上增量开发的设计。Vue 的核心库只关注视图层，并且非常容易学习，非常容易与其它库或已有项目整合。另一方面，Vue 完全有能力驱动采用单文件组件和Vue生态系统支持的库开发的复杂单页应用
- **Backbone**为复杂Javascript应用程序提供模型(models)、集合(collections)、视图(views)的结构。其中模型用于绑定键值数据和自定义事件；集合附有可枚举函数的丰富API； 视图可以声明事件处理函数，并通过RESTful JSON接口连接到应用程序。
- **Underscore**是一个 JavaScript 工具库，它提供了一整套函数式编程的实用功能，但是没有扩展任何 JavaScript 内置对象。 他解决了这个问题：“如果我面对一个空白的 HTML 页面，并希望立即开始工作，我需要什么？” 他弥补了 jQuery 没有实现的功能，同时又是 Backbone 必不可少的部分。
- **D3.js** 数据可视化和图表是web应用程序的一种常规需求。当涉及到任何数据操作和可视化时，D3.js 就是事实上的标准。它是 GitHub 上最受欢迎的项目之一，并被数百个组织机构所采用。大量的图形、图标和可视化库都是构件于 D3 之上的。
D3 让你可以操作任何来源的数据文档，并将数据进行转换后应用到 DOM、SVG 和 CSS上。D3 专注于现代的 web 标准，以及确保你可以不受到任何像 Flash 或者 Silverlight 这样的专有格式的限制。
- **YUI**，是雅虎公司开发的一套完备的、扩展性良好的富交互网页工具集。 
- **Prototype**，是最早成型的 JavaScript 库之一，对 JavaScript 内置对象做了大量的扩展。
- **Dojo**，Dojo 强大之处在于提供了其他库没有的功能。离线存储、图标组件等等。 
- **Mootools**，轻量、简洁、模块化和面向对象的 JavaScript 框架。 
- **ExtJS**，简称 Ext，原本是对 YUI 的一个扩展，主要创建前端用户界面。(付费的)

### jquery 基本结构

~~~
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title></title>
		<script src="js/jquery-1.10.1.js" ></script>
		<script>
    		$(function(){
                 //所有的js操作都放在这个 方法里面		
    		})
		</script>
	</head>
	<body>
		<h1>内容</h1>
	</body>
</html>

~~~
一个页面只要引用 一个 jquery-*.js文件即可