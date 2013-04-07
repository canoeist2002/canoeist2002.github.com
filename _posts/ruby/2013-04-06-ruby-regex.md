---
layout: post
title: "ruby regex"
description: "ruby regex"
category: ruby
tags: [ruby, program]
---
{% include JB/setup %}

正则表达式是非常重要的一个工具，在任何编程语言中，都会使用它来进行对文本的匹配，而且它也是非常用到的一个工具，掌握好正则表达式的使用非常重要。

## 基本用法

正则表达式经常和字符串方法结合使用，不过，我们还是先了解一下最基本的自身用法。那先认识一个叫做 =~ 的操作符，它就是正则匹配的操作符，它是这样使用的：

    >> /o/ =~ 'hello world'           # => 4
    >> /ol/ =~ 'hello world'          # => nil

如果发现了有匹配项，ruby 就回返回在字符串中哪一个位置匹配的，而没有匹配则回返回 nil。在 ruby 中，你也可以在 =~ 符的左边放字符串，右边放正则表达式：

    >>  'hello world' =~ /o/          # => 4

一般都喜欢使用上面的那种做法，也即正则表达式放在 =~ 符的左边。同样，正则表达式也可以放入到一个变量中，然后要使用的时候调用，就像下面这种方法使用：

    >> pattern = /o/
    >> pattern =~ 'hello ruby'        # => 4
    >> pattern =~ 'the new world'     # => 9

还有常用的方法是使用 match() 方法，用法是 pattern.match(str) ，有匹配的话则返回 MatchData ，不然就返回 nil：

    >> r = /o/.match('hello world')   # => #<MatchData "o">
    >> r.class                        # => MatchData

## 正则表达式语法

这里一个庞大的、复杂的部分，还好，可以一步一步从简单的开始，掌握好了再逐步的去掌握更复杂的模式，而这种正则表达式语法可以使用到多种编程语言中，包括 python，java，和像 bash 一样的脚本语言中，并且，在 linux 的命令中也是要以使用的。

<p>这里从最基本的 [] 开始，它是使用过程中最常用到的方法，用法如下： </p>

    >> /[aeiou]/.match('hello world') # => #<MatchData "e">  匹配元音字符
    >> /[a-z]/.match('hello world')   # => #<MatchData "h">  匹配小写字母
    >> /[0-9]/.match('hello world')   # => nil               匹配数字

然后，再在上面的基础上加点通配符，它们是：

    .     匹配任何的 1 个字符
    ?     匹配 0 个或者是 1 个
    *     匹配 0 个或者是多个
    +     匹配 1 个或者是多个

    >> /[a-z]?/.match('hello world')  # => #<MatchData "h">
    >> /[a-z]*/.match('hello world')  # => #<MatchData "hello">
    >> /[a-z]+/.match('hello world')  # => #<MatchData "hello">

上面的 [a-z]? 这个表达式装匹配任意的小写字母，或者是没有，也可能匹配成功，比方说：

    >> /[a-z]?/.match('')             # => #<MatchData "">
    >> /[a-z]?/.match('0')            # => #<MatchData "">
    >> /ruby?/.match('ruby')          # => #<MatchData "ruby">  匹配 rub 也会成功

一般常用的是 + 号比较多点，它可以用来匹配，比方说用户名：

    >> /[a-zA-Z0-9_]+/.match('ruby')                 # => #<MatchData "ruby">
    >> /[a-zA-Z0-9_]+/.match('example@hotmail.com')  # => #<MatchData "example">

当然，老是 [a-zA-Z0-9] 或 [0-9] 这样常用到的匹配模式，正则表达示也为什么准备了一些方法来简化，可以使用：

    \d     匹配数字，也就是 0-9
    \s     匹配空白字符，换行回车什么的
    \w     匹配单词，和 [a-zA-Z0-9_] 是一样的

它们的大写形式，\D、 \S、 \W 是取这些字符的反，比如 \D 就是除 0-9 以外的任意字符。

    >> /\w+/.match('example@hotmail.com')          # => #<MatchData "example">

还有行首和行尾匹配，^ 是行首，$ 是行尾，比方说上面的那个 /\w+/..match('example@hotmail.com') 去匹配 example@hotmail.com，但如果前面还有其它字符的话，也会匹配成功，比如：

    >> /\w+/..match('***example@hotmail.com')      # => #<MatchData "example">

这时就需要加入行首限定符了，开头必须是要以 [a-zA-Z0-9_] 这部分的内容：

    >> /^\w+/.match('example@hotmail.com')         # => #<MatchData "example">

另外，还有 \A 匹配字符串开始 和 \z 匹配字符串结尾。

正则表达式的最基咄的部分就这些了，后面将会绘写一点比较复杂的内容。


## 参考资料

正则表达式匹配查询 [Rubular](http://rubular.com/)

