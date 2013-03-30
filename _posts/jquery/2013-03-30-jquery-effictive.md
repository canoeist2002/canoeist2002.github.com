---
layout: post
title: "jQuery Effictive"
description: "jQuery Effictive"
category: jquery
tags: [web, jquery]
---
{% include JB/setup %}

效果是 jQuery 里的一大特色，通过使用各种不同的效果，而达到吸引浏览者注意力，增加页面美感的功能。

## 修改内联 CSS

虽然我们可以通过前面用到的 .addClass() 和 .removeClass() 来添加和移除元素相应的 CSS，但有时我们需要直接的去设置没有在样式表中定义的样式时，可以使用 .css() 方法来完成。它的语法是：

* .css('property', 'value')
* .css({'property1': 'value', 'property2': 'value2'})

比如这里可以为 #header 的 ID 设置它的字体大小：

    $('#header').css('fontSize', '2 em')

## 基本的隐藏和显示

jQuery 提供了两个方法，一个是 .hide() 一个是 .show()，当调用 .hide() 方法的时候，jQuery 会记住调用对象的 display 值，一般来说是 block 或者是 inline ，主要是为了方便执行 .show() 的时候不会导致显示出现问题，比如 li 做的导航。同时它会把 display 值设置为 none。

    $('li.eq(1)').hide()

## 效果和速度

在上面的方法 .show() 和 .hide() 中，可以指定一个速度参数，会产生动画的，值可以是 slow （0.6 秒），normal （0.4秒） 和 fast （0.2秒）。当然你也可以指定时间，以毫秒数来计，比如：.show(850)

此外，还可以使用淡入和淡出的效果， .fadeIn() 和 .fadeOut() ，同样，也可以指定速度参数。

## 自定义动画效果

除此之外，可以使用 jQuery 提供的 .animate() 方法来自定义动画，不过这么高级的功能一般我是用不上的，只能用好别人写好的动画效果就行了。

## 总结

这里我们讲到了一些最常用的 jQuery 效果，比如使用 .css() 方法给指定的元素添加样式，或使用 .hide() 和 .show() 方法来隐藏和显示元素。
