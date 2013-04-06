---
layout: post
title: "ruby string"
description: "ruby string"
category: ruby
tags: [ruby, program]
---
{% include JB/setup %}

字符串是应用程序中最最常用到的部分了，大多数应用程序中，字符串对象占用的比例都超过了 50%，全面的理解和合理的使用字符串才不会使用你的应用程序占用过多的内存。所以，了解字符串如何在程序里的使用也是至关重要的。

## 字符串创建

字符串通常都是使用引单来创建的，在 Ruby 中，使用 ' 单引号和使用 " 双引号创建的字符串是不一样的。使用单引号创建的字符串是最简单形式的字符串，什么意思呢？其它它是和双引号的字符串的比较来说的，过不了多久你就可以明白了。

    >> 'This is new string.'            # => "This is new string."

字符串就是这样被创建出来的，这谁都知道。如果字符串是这样的 'This's new string.' 你去创建看看，里面一个单引号，这样，ruby 就不知道哪哪一个单引号是结束标记了。这个时候应该这样：

    >> 'This\'s new string.'            # => "This's new string."

在这里，加上了一个反斜线做为转码标记，一般来说，在单引号引用的字符串中，如果你要使用单引号和反斜线，就要使用反斜线进行转义。

    >> 'a\b' == 'a\\b'                  # => true

而由双引号引用的字符串可以支持更多的转义，比如 \t talbe 符号，\n 换行符，等等都可以支持。可以在双引号引用的字符串变量中放入单引号而无须转义。

    >> s = "The new string.\nIt's greate!"  # => "The new string.\nIt's greate!"
    >> puts  s                              # => The new string.
                                                 It's greate!

双引号引用的字符串除了支持各种转义符外，还支持字符串内插值，它是 #{} 来表示的，非常的常用：

    >> num = 4 
    >> "Num is a #{num}"                # => "Num is a 4"
    >> "PI is #{Math::PI}"              # => "PI is 3.141592653589793"

<p>Ruby 中还支持一种采用 %q 和 %Q 来引导的字符串变量，%q 使用的是单引号引用规则，而 %Q 是双引号引用规则，后面再接一个 ( [ {  等等的开始界定符和与  } ] ) 等等的末尾界定符，</p>

    >> %q(This's new string.)               # => "This's new string."
    >> %Q<The new string.\nIt's great!>     # => "The new string.\nIt's great!"

## 字符串基本操作

如果想要连接两个字符串的，一种最简单的方式是使用 + 运算符来操作，用它来连接字符串，但要注意一点的是，它只能用来连接字符串，不能连接字符串和数字这样的结构，必须使用 to_s() 转换才行：

    >> "Hello" + " " + "world"          # => "Hello world"
    >> "Hello" + " " + 123.to_s         # => "Hello 123"

当然，最方便的还是使用刚才的字符串内插的方法，它可以自动的调用 to_s() 来进行转换，就像刚才我们使用的那个例子一样。另外，使用 << 操作符也是非常使得的方法：

    >> word = "Hello"                   # => "Hello"
    >> word << " "                      # => "Hello "
    >> word << "Ruby"                   # => "Hello Ruby"

字符串就是字符和合集，可以当做数组来操作：

    >> s = 'hello'
    >> s.length                         # => 5  同样的方法还有 size()
    >> s[0]                             # => "h"
    >> s[-1]                            # => "o"
    >> s.each_char{|a| print a}         # hello  each_char() 返回单个字符

## 字符串常用 API

Ruby 提供了大量的字符串相关 API 来方便开发者使用，

### include?() 和 index()

使用 include?() 方法来查找字符串是否包含有指定的对象，返回值为 ture 或者是 false;而 index() 则会返回找到的对象位于第几个元素。

    >> s = "hello"
    >> s.include? "e"                   # => true
    >> s.include? "a"                   # => false
    >> s.index("d")                     # => nil
    >> s.index("o")                     # => 4

### start_with?() 和 end_with?()

如果在开头的位置找到指定的对象则返回 ture ，否则返回 false。而另一个方法是在最后的位置查找：

    >> s = "hello"
    >> s.start_with?("he")              # => true
    >> s.end_with?("oo")                # => false

### sub() 和 gsub()

这两个方法都是替代字符串中的相对应的对象的，第一个 sub() 方法是替换到找到的第一个对象，而 gsub() 则是替换所有的找到的对象。当然可以使用正则表达式来进行强大的匹配，在以前的正则表达式的部分在详细的了解。同时，它们也都还有一个还有 ! 的方法，用来改变原来的字符串对象：

    >> s = "hello"
    >> s.sub('l','*')                   # => "he*lo"
    >> s.gsub('l','*')                  # => "he**o"
    >> s.gsub(/[aeiou]/, '*')           # => "h*ll*"

### strip()， lstrip() 和 rstrip()

这三个方法都是去掉字符串对象中开头的或结尾部分的空白符（空格，回车和换行），中间的空格是不会给去掉的。strip() 是去掉两边的空白符，lstrip() 是左边的空白符，而 rstrip() 是右边的空白符。它们都有对应的 ! 方法：

    >> s = "   hello   "
    >> s.strip                          # => "hello"
    >> s.lstrip                         # => "hello   "
    >> s.rstrip                         # => "   hello"

### chomp() 和 chop()

这两个方法是用于去除字符串对象后面的符号的，chop() 是去除最后一个符号，这个不太常用，而 chomp() 是去除字符串后面的 \r，\n 或是 \r\n，常用于获取用户输入后，去掉最后的那个回车符。

    >> a = "hello\r"                    
    >> a.chomp                          # => "hello"
    >> s = gets.chomp                   # 获得用户输入，并去掉最后的回车符

### split()

该方法可以根据指定的对象来分隔字符串，果然没有指定字符串的话则会使用空格来分隔字符串，它将始终会返回数组对象：

    >> "Ruby is greate".split           # => ["Ruby", "is", "greate"]
    >> "1,2,3,4".split(",")             # => ["1", "2", "3", "4"]

### upcase(), downcase() 和 capitalize()

这几个方法可以改变字符串在的大小字，而 capitalize() 是将首字符大写，后面的字符小写；同时这几个方法也有带 ! 的方法，可以将返回结果覆盖到自身：

    >> "Ruby is greate".downcase        # => "ruby is greate"
    >> "Ruby is greate".upcase          # => "RUBY IS GREATE"
    >> "Ruby is greate".capitalize      # => "Ruby is greate"

### ljust(), rjust() 和 center()

可以按对齐的方法输出字符串，用的比较少：

    >> "ruby".center(20)                 # => "        ruby        "

### count()

记数方法，可以统计指定的字符串出现的数量：

    >> "Ruby is greate".count("r")      # => 1
    >> "Ruby is greate".count(" ")      # => 2

### to_i(), to_f(), to_sym(), to_complex()

将字符串对象转换成指定的格式，i 是整数，f 是浮点数，sym 是 hash 中用的符号，complex 是复数：

    >> "10".to_i                        # => 10
    >> "a10a".to_i                      # => 0
    >> "10a".to_i                       # => 10

## 参考资料

* Ruby 1.9.3  [String](http://www.ruby-doc.org/core-1.9.3/String.html)
