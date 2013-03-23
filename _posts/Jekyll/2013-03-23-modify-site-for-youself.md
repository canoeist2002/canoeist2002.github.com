---
layout: post
title: "Modify Site for youself"
tagline: "自定义网站的内容"
description: "Jekyll Bootstrap Github"
category: tutorial
tags: [Jekyll]
---
{% include JB/setup %}

现在，我们已经有了一个可以使用的网站了，但目前我们的站点还是默认的站点样式，现在我们通过一些简单的修改来自定义相关的内容。在这里，我们将了解到：

* 如何自定义导航条
* 发表 post

## 一、发表一个 Post

<p><span class="badge badge-important">1</span>　使用如下命令来创建一个 Post：</p>

   $ rake post title = "Hello world"

<p>该命令会自动的在 _posts 目录下面生成一个以日期开头的文件，就样这样的格式 2013-03-23-hello-world.md ，这种 md 文件可以使用 Markdown 的方法来编辑，也可以使用 HTML 格式来编辑，非常方便。</p>

<p><span class="badge badge-important">2</span>　设置文件头，使用你喜欢的文本编辑器来打开文件，我用的是 sublime 这款免费、功能强大的编辑器，首先修改文件头里的信息：</p>

    ---
    layout: post
    title: "Build this site on Github"
    description: ""
    category: 
    tags: []
    ---
    {% include JB/setup %}

根据需要，加上你想上的内容，category 是该 Post 属于什么类别，tags 当然就是标签了，推荐使用英文来完成。

<p><span class="badge badge-important">3</span>　编辑文件，你可以在里面输入任何的内容了，使用 markdown 格式和 HTML 格式都可以，混合写都行。你可以通过本地的 Jekyll 站点来查看效果。</p>