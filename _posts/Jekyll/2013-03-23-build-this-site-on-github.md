---
layout: post
title: "Build this site on Github"
tagline: "如何创建本网站"
description: "Jekyll Bootstrap Github"
category: tutorial
tags: [Jekyll]
---
{% include JB/setup %}

我们将在这里学到如何在 github 上构建自己的网站，它可以是你喜欢的任何网站，也可以是一个 BLOG 系统，在篇文章中我们将学会：

<ul>
<li> 如何使用 Jekyll 在 github 上建立网站 </li>
<li> 如何在本地运行和调试网站 </li>
<li> 定义站点的基本结构 </li>
<li> 上传网站到 github </li>
</ul>

## 一、入门

我们可以使用 Jekyll 在 github 上建立站点，但是功能和界面全部都没有，还得要自己去做，而使用 [jekyllbootstrap](http://jekyllbootstrap.com/) 就非常的方便了，它集成了很多的功能和 [Bootstrap](http://twitter.github.com/bootstrap/) 来美化界面，就非常方便了。

<p><span class="badge badge-important">1</span>　创建 Repository
我们需要去 [Github](https://github.com/) 上创建一个新的 Repository，这个 Repository 的名称为 USERNAME.github.com，其中的 USERNAME 是你的 github 账号的名称。完成教程之后就可以通过 USERNAME.github.com 来访问了！</p>

![创建新的 Repository](/images/tutorial/Create-a-new-repository-on-github.png)

<p><span class="badge badge-important">2</span>　现在，你可以通过下面的命令来下载 jekyllbootstrap 了，并把它上传到你自己的 github 上面了。</p>

    git clone https://github.com/plusjade/jekyll-bootstrap.git USERNAME.github.com
    $ cd USERNAME.github.com
    $ git remote set-url origin git@github.com:USERNAME/USERNAME.github.com.git
    $ git push origin master

<p><span class="badge badge-important">3</span>　大概等 10 分钟之后，你就可以通过使用 http://USERNAME.github.com 来访问你的自己的网站了。</p>

## 二、本地运行

我们可以在本地查看编辑的效果，如果满意的话，就可以上传到 github 上。

<p><span class="badge badge-important">1</span>　首先，你需要安装 jekyll 。</p>

    $ gem install jekyll

<p><span class="badge badge-important">2</span>　然后，你可以运行命令：</p>

    $ cd USERNAME.github.com 
    $ jekyll --server

这个时候，你就可以通过 http://localhost:4000/ 来访问你自己的本地站点了，你将可以看到下面的内容：

![Jekyll Bootstrap 的默认站点](/images/tutorial/default-site-for-jekyll-bootstrap.png)

## 三、与中文相关的问题

你肯定是要在网站中输入与中文相关的内容的，但启动 server 的时候会出错下面的错误提示

    Liquid Exception: incompatible character encodings: UTF-8 and GBK in post

这个时候可以这样解决：

<p><span class="badge badge-important">1</span>　首先，打开 jekyll 的 lib 文件，<span class="text-error">convertible.rb </span>，我用的是 windows 7 系统，在 C:\RailsInstaller\Ruby1.9.3\lib\ruby\gems\1.9.1\gems\jekyll-0.12.1\lib\jekyll 这个目录下面。</p>

<p><span class="badge badge-important">2</span>　然后将该文件的 28 行：</p>

    self.content = File.read(File.join(base, name))

<p>改成：</p>

    self.content = File.read(File.join(base, name), :encoding => "utf-8")

## 四、自定义网站基本信息

<p>打开目录中的 _config.yml 文件，会看到如下的内容：</p>

    title : Jekyll Bootstrap
    tagline: Site Tagline
    author :
      name : Name Lastname
      email : blah@email.test
      github : username
      twitter : username
      feedburner : feedname

从字面意识上就很容易理解了，其中的那个 tagline 就是大标题后面跟着的那个字体稍微淡点的副标题。再下面一点，有个

    production_url : http://username.github.com

把 username 改成你自己的名字就行了。

## 五、上传到 github

<p><span class="badge badge-important">1</span>　发布内容，可以使用 git 的命令来完成，和使用 git 管理其它的开源项目是一样的：</p>

    $ git add .
    $ git commit -m "Add new content"
    $ git push origin master

<p><span class="badge badge-important">2</span>　现在，你就可以通过 USERNAME.github.com 来访问了，内容等你上传完就会更新了，不用第一次建站需要等待十分钟左右的时间了，看到的效果和你在本地看到的效果是一样的。</p>


## 参考资料

* Jekyll [Github 站点](https://github.com/mojombo/jekyll)
* Jekyllbootstrap [Jekyllbootstrap 主页](http://jekyllbootstrap.com/)
* Jekyllbootstrap [Github 站点](https://github.com/plusjade/jekyll-bootstrap)
* Markdown [Markdown 语法](http://daringfireball.net/projects/markdown/syntax)