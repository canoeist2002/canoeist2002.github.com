---
layout: post
title: "jQuery basic concept"
description: "jQuery basic concept"
category: jquery
tags: [web, jquery]
---
{% include JB/setup %}

比起 javascript 复杂难忘的语法， jQuery 用起来令人惬意多了，虽然它本身就是一个使用 javascrip 开发出来的库，但其强大的功能，方便的 DOM 操作，使其在几乎现阶段所有的网页中都有不同程度的使用。而使用 jQuery 可省去了使用　Javascript 那样的麻烦，虽然如此，但一般来说还是要学点 javascript 的语法的。

这里记录下了我学习 jQuery 中最重要的内容和过程，当然首先是从哪些地方找到这样学习材料：

* 图书《jQuery 基础教程》
* 在线学习网站 [codecademy](http://www.codecademy.com/)
* 官方网站  [jQuery](http://jquery.com/)

这里我是从 jQuery 1.9.1 这个版本来做演示的，下面是最基本的演示文件：

    <!DOCTYPE html>
    <html>
      <head>
        <meta charset="utf-8">
        <title>JQuery 练习页面</title>
      </head>
      <body>
        <h1>Hello, JQuery!</h1>
        <p>JQuery 是一个非常优秀的 Javascrip 框架。</p>

        <script src="javascript/jquery-1.9.1.js"></script>
      </body>
    </html>

如果你在网站中部署 jQuery 的话，可以使用 CDN 网络来加快 jQuery 的载入速度：

    //ajax.googleapis.com/ajax/libs/jquery/1.9.1/jquery.min.js

好，马上开始。