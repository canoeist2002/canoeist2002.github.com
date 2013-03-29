---
layout: post
title: "jQuery Event"
description: "jQuery Event"
category: jquery
tags: [web, jquery]
---
{% include JB/setup %}

jQuery 提供了很多的事件响应方式来增强 javascript 里原来就有的响应方式，非常更于大家的使用。


## $(document).ready()

该方法在上面已经介绍过，它最主要的功能就是在页面的 DOM 载入完成后执行。它和页面载入完成是有区别的，比如一个页面上面有很多的视频和图片的话，一般来说，页面的 DOM 结构在整个页面的大小中所占的比例是非常小的，这就是说，不用长时间的等待视频和图片加载完成，而此时 jQuery 就可以使用了。

    $(document).ready(function(){
      // do something
    });

是最常用的使用方式了，document 是可以省略的，所以这里的代码也可以写成：

    $().ready(function(){
      // do something
    });

当然，jQuery 也会默认的去执行一次 .ready() 调用，那也就是说，下面的方法是同样的效果：

    $(function(){
      // do something
    });

一般来说，虽然可以简写使用，但绝大多数的工程师还是倾向于采用完整的写法，因为这种写法更便于人类的阅读，毕竟代码还是会给人来维护的。

## 简单事件

jQuery 使用改进的 javascript 事件方法来触发事件，它使用  .bind() 来添加一系列的动作。比如：

    $('#button').bind('click', function(){
      $('body').removeClass('large');
    });

当单击一个 ID 名称为 button 的元素时，则移除 body 标签里面 .large CSS。同样，你也可以使用 jQuery 中提供的更简单易懂的 click() 方法来代替 bind() ：

    $('#button').click(function(){
      $('body').removeClass('large');
    });


## 复合事件

对于触发事件后，以多个函数作为响应的事件，称为复合事件。最常见的是 .toggle() 和 .hover() 这两个方法。

这里的 .toggle() 方法接受两个函数作为参数，当第一次单击时执行第 1 个函数，第二次单击里执行第 2 个函数，比如：

    $(document).ready(function(){
      $('#button').toggle(function(){
        $('#button .button').addClass('hidden');
      },function(){
        $('#button .button').removeClass('hidden');
      });
    });

由于这个方法太常用了，所以，jQuery 为我们提供了一个自己检查该类是否存在的方法 .toggleClass() ：

    $(document).ready(function(){
      $('#button').click(function(){
        $('button .button').toggleClass('hidden');
      });
    });

而 .hover() 方法则是一个和 :hover 这个 CSS 伪类选择器差不多的方法，当鼠标进入和移出元素时的操作。


## 模仿用户操作

有的时候我们需要去模仿用户的操作，比如点击某个元素：

    $(document).ready(function(){
      $('#button').trigger('click');
    });

或者也可以使用更简单的方法：

    $(document).ready(function(){
      $('#button').click();
    });


## 总结

事件是 jQuery 里面一个重要的内容，也是触发整个 jQuery 行为的基础，根据不同的触发事件响应不同的动作。
