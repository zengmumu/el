

### jquery 插件

  
在实际开发工作中，总会碰到像滚动，分页，日历等展示效果的业务需求，对于接触过`jQuery`以及熟悉`jQuery`使用的人来说，首先想到的肯定是寻找现有的`jQuery`插件来满足相应的展示需求。目前页面中常用的一些组件，都有多种`jQuery`插件可供选择，网络上也有很多专门收集`jQuery`插件的网站。利用`jQuery`插件确实可以给我们的开发工作带来便捷，但是如果只是会简单使用，而对其中的原理不甚了解，那么在使用过程中碰到问题或者对插件进行定制开发时就会有诸多疑惑。本文的目的就是可以快速了解`jQuery`插件的开发原理以及掌握`jQuery`开发的基本技能。

进行`jQuery`插件开发前，首先要知道两个问题：什么是`jQuery`插件？`jQuery`插件如何使用？  
第一个问题，`jQuery`插件就是用来扩展`jQuery`原型对象的一个方法，简单来说就是`jQuery`插件是`jQuery`对象的一个方法。其实回答了第一个问题，也就知道第二个问题的答案了，`jQuery`插件的使用方式就是`jQuery`对象方法的调用。

我们先看个例子：`$("a").css("color","red")`。我们知道每个`jQuery`对象都会包含`jQuery`中定义的`DOM`操作方法,这里使用`$`方法来选择`a`元素，返回一个`a`元素的`jQuery`对象，这个对象就可以使用`jQuery`中定义的`DOM`操作方法。那么`jQuery`对象是如何获取这些方法的呢？其实`jQuery`内部定义了一个`jQuery.fn`对象，查看`jQuery`源码可以发现`jQuery.fn=jQuery.prototype`，也就是说`jQuery.fn`对象是`jQuery`的原型对象,`jQuery`的`DOM`操作方法都在`jQuery.fn`对象上定义的，然后`jQuery`对象就可以通过原型继承这些方法。

**基础版jQuery插件**  
知道了上面这些知识，我们就可以来写一个简单的`jQuery`插件。假如我现在需要一个`jQuery`插件用来改变标签内容颜色，就可以按下面的方式来实现这个插件：



    
    
    $.fn.changeStyle = function(colorStr){
                     this.css("color",colorStr);
            }
            

然后按下面的方式来使用插件：  
`$("p").changeStyle("red");`  
插件调用的时候，插件内部的`this`就是当前调用插件的`jQuery`对象，这样的话每个使用`$()`方法选择的标签，在调用`changeStyle()`插件时都会使用`css()`方法重设`color`样式。

**满足链式调用的jQuery插件**  
链式调用时`jQuery`的一大特色，一个通用的插件应该遵循`jQuery`风格，满足链式调用要求。实现链式调用的方式也很简单：

__

    
    
    $.fn.changeStyle = function(colorStr){
                     this.css("color",colorStr);
                     return this;
            }
            

然后使用的时候就可以链式调用其他方法了：  
`$("p").changeStyle("red").addClass("red-color");`  
实现链式调用的关键点就一行代码`return
this`，插件中加了这行代码，那么在插件执行完之后，就会把当前的`jQuery`对象返回，然后就可以在插件方法后面继续调用其它`jQuery`方法。

**防止符号污染的jQuery插件**
有很多`js`库都会使用``符号，虽然`jQuery`可以使用`jQuery.noConflict()`方法交出$符号的使用权，但是如果定义插件的时候，使用`.fn`对象来定义的，那么这些插件使用的时候就会受到其它使用``变量的`js`库的影响。对于这种情况，我们可以使用立即执行函数通过传参的方式封装插件。形式如下：

__

    
    
    ( function($){
                 $.fn.changeStyle = function(colorStr){
                     this.css("color",colorStr);        
                     return this;
                 }
            }(jQuery));
            

因为使用了立即执行函数，所以此时的`$`只属于这个立即执行函数的函数作用域，这样就可以避免`$`符号的污染。

**可以接受参数的jQuery插件**  
继续上面的例子，假如我还想为这个插件添加一个设置标签元素内容文字大小的功能，那么我可以这么来实现：

__

    
    
    ( function($){
                 $.fn.changeStyle = function(colorStr，fontSize){
                     this.css("color",colorStr).css("fontSize",fontSize+"px");        
                     return this;
                 }
            }(jQuery));
            

上面这种插件传参方式适用于参数比较少的情况，如果需要传给插件内部的参数比较多，我们可以定义一个参数对象，然后把需要传给插件的参数放在参数对象中。插件定义时如下：

__

    
    
    ( function($){
                 $.fn.changeStyle = function(option){
                     this.css("color",option.colorStr).css("fontSize",option.fontSize+"px");        
                     return this;
                 }
            
            }(jQuery));
            

使用方式：`$("p").changeStyle({colorStr:"red",fontSize:14});`  
把参数放到一个对象中传给插件还有一个好处就是我们可以在插件内部为一些参数定义一些缺省值，例如：

__

    
    
    ( function($){
            
                 $.fn.changeStyle = function(option){
                      var defaultSetting = { colorStr:"green",fontSize:12};
                      var setting = $.extend(defaultSetting,option);
                      this.css("color",setting.colorStr).css("fontSize",setting.fontSize+"px");        
                     return this;
                 }
            }(jQuery));
            

上面的代码用到了`$.extend`方法，这个方法在这里的用法就是合并两个对象，即把后面一个对象的存在的属性值赋值给第一个对象，具体用法可以参考[这里](http://www.php100.com/manual/jquery/jQuery.extend.html)。`$.extend`方法还有一种作用是用来扩展`jQuery`对象本身。  
这样定义的插件，我们在使用时如果不传`fontSize`，那么使用这个插件的`jQuery`对象标签的内容会被设置成默认的`12px`。  
使用方式：`$("p").changeStyle({colorStr:"red"});`  
注意：在为插件定义默认参数时，一定要把默认参数写在插件方法内部，这样默认参数的作用域就在插件内部。

**总结**  
定义插件的方式除了上面说的用`$.fn`来定义，还有另外一种方式来定义插件，那就是使用`$.fn.extend`方法。类似下面的写法：

__

    
    
    ( function($){
                 $.fn.extend({         
                     changeStyle:function(option){             
                     var defaultSetting = { colorStr:"green",fontSize:12};
                     var setting = $.extend(defaultSetting,option);
                     this.css("color",setting.colorStr).css("fontSize",setting.fontSize+"px");        
                     return this; 
                      }
                 });
            }(jQuery));
            

>
> PS:`$.extend`方法和`$.fn.extend`方法都可以用来扩展`jQuery`功能，通过阅读`jQuery`源码我们可以发现这两个方法的本质区别，那就是`$.extend`方法是在`jQuery`全局对象上扩展方法，`$.fn.extend`方法是在`$`选择符选择的`jQuery`对象上扩展方法。所以扩展`jQuery`的公共方法一般用`$.extend`方法，定义插件一般用`$.fn.extend`方法。

