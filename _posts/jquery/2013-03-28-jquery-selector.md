---
layout: post
title: "jquery selector"
description: "jquery selector"
category: jquery
tags: [web, jquery]
---
{% include JB/setup %}

使用 jQuery 选择器可以非常方便的在 DOM 中选择你想要操作的内容，而且也有很多的方法来使你非常方便选择既定的部分。

## $(document).ready()
jQuery 中最常使用到的内容，就是在文件的 DOM 元素加载完成后执行 ready() 里面的内容，比如：

    $(docutment).ready(function(){
      alert("Hello jQuery!");
    });

会弹出一个上面显示 "Hello jQuery" 的对话框。

## $()
最基本的情况下，使用 $() 符号来选择 html 文件中的对象：

* 选择标签：$('p')
* 选择 ID ：$('#id-name')
* 选择 class：$('.class-name')

