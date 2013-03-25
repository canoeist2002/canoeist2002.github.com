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

<ul>
<li>删除演示页面 </li>
<li>如何自定义导航条 </li>
<li>发表 post 和 page </li>
<li>了解 post 和 page </li>
</ul>
## 一、删除演示页面

为了演示网站的用法和基本的 Markdown 的语法，Jekyll Bootstrap 准备了一个演示页面，你可以看看大致的语法是什么样的、category 和 tags 是怎么写的。当然，在你自己的站点上你可能需要把它删除。

<p><span class="badge badge-important">1</span>　使用资源管理器或命令将 _post/core-samples 目录给删除掉，同时删除的还有里面的一个文件，2011-12-29-jekyll-introduction.md。</p>

<p><span class="badge badge-important">2</span>　在 git 的本地仓库里也将将目录删除，使用命令 git rm -r _post/core-samples。</p>

<p><span class="badge badge-important">3</span>　然后，使用命令提交变动：</p>

    $ git add .
    $ git commit -m "delete demo file and directory"
    $ git push

## 二、自定义首页内容和导航条

现在，我们可以看到右上角自动生成的那个导航栏了，这个导航栏现在是 Archive Categories Pages Tags，我们可以根据自己的需要去定制它的内容，想要去添加一个 about。我们应该生成 page ，page 的内容不会被自动的生成到 archive 分类中，而 categories 和 tags 是关于 archive 内容的。

<p><span class="badge badge-important">1</span>　生成 Page。使用如可以使用命令：</p>

    $ rake page name="about.html"

或者自己去手动的去创建文件。两种方法都行。文件可以是 about.me 或都是 about.html。

<p><span class="badge badge-important">2</span>　文件内容，不管你是使用命令生成或都是自己创建的文件，里面都要有这样的内容：</p>

    ---
    layout: page
    title: "About"
    description: ""
    ---
    {% include JB/setup %}

要显示到导航条上，就要在上面的 description 的下面加上：

    group: navigation

系统自动就会在导航条上显示出来了，如果你不想要某个项目，比如 tags，那你就可以在 tags.html 这个文件中将 group: navigation 删除掉就行了。


## 三、发表一个 Post

现在，是时候来发表自己的第一个 Post 了。

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

根据需要，加上你想上的内容，category 是该 Post 属于什么类别，tags 当然就是标签了，多个 tag 中间使用 “,” 去分隔就行了。

<p><span class="badge badge-important">3</span>　编辑文件，你可以在里面输入任何的内容了，使用 markdown 格式和 HTML 格式都可以，混合写都行。你可以通过本地的 Jekyll 站点来查看效果。</p>

## 四、主页内容

现在，对于 Jekyll 的简单的操作和设置你应该都知道了，同样，主页的内容也是很简单定制的，你可以通过编写 index.md 中的内容，来达到定制自己首页的内容。

## 参考资料

* Jekyll [Github 站点](https://github.com/mojombo/jekyll)
* Jekyllbootstrap [Jekyllbootstrap 主页](http://jekyllbootstrap.com/)
* Jekyllbootstrap [Github 站点](https://github.com/plusjade/jekyll-bootstrap)
* Markdown [Markdown 语法](http://daringfireball.net/projects/markdown/syntax)

