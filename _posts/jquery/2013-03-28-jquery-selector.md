---
layout: post
title: "jQuery Selector"
description: "jQuery Selector"
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

## XPath 选择符
XPath （XML Path Language，XML 路径语言）是 XML 文档中识别不同的元素或值的，与 CSS 使用的方式类似。

比如要选择所有的带 title 属性的链接，可以使用：

    $('a[@title]')

也可以结合使用正则表达式来选择，比如下面的几个例子：

    * $('a[@href^="mailto:"]') 为选择链接标签中的 href 属性里以 mailto: 开头的链接
    * $('a[@href$=".pdf"]') 为选择链接标签中的 href 属性里以 .pdf 结尾的链接
    * $('a[@href*="mysite.com"]') 为选择链接标签中的 href 属性里带有 mysite.com 的链接

## 自定义选择符
除了 CSS 和 XPath 选择符外，jQuery 自带了一些特殊的选择符，这些选择符一般使用 : 来标识。

    * $('p:eq(1)')   选择第两个 p 标签
    * $('tr:odd')  选择 tr 标签的奇数行
    * $('tr:even')  选择 tr 标签的偶数行
    * $('td:contains("Henry")')  选择 td 标签中含有 "Henry" 内容的标签

注意：javastrip 是以 0 开始计数的，所以 jQuery 中也是使用 0 开始。

## DOM 遍历方法

    * $('tr:not([th]):odd')
    * $('td:contains("Henry")').siblings().addClass('highlight')  选择出所有包含 Henry 内容的同类标签并添加样式
    * $('td:contains("Henry")').parent().find('td:gt(0)').addClass('highlight')

同时这也是 jQuery 中的连缀使用。

## 总结

选择器是在网页开发的过程中经常性会用到的内容，可以从最简单的 CSS 选择器开始学习和使用，然后，再慢慢的熟悉比较复杂的 XPath 和 jQuery 自定义选择器的使用。
