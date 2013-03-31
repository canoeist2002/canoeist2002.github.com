---
layout: post
title: "jquery dom and ajax"
description: "jquery dom and ajax"
category: jquery
tags: [web, jquery]
---
{% include JB/setup %}


## DOM 操作方法

jQuery 中提供了大量的对 DOM 的操作方法，可以完成各种不同的功能，要适当的情况下选择不同的方法吧：

1. 在每个匹配的元素中插入新元素

    * .append()
    * .appendto()
    * .prepend()
    * .prependTo()

2. 在每个匹配的元素相邻的位置插入新元素

    * .after()
    * .insertAfter()
    * .before()
    * .insertBefore()

3. 在每个匹配的元素外部插入新元素

    * .wrap()

4. 用新的元素或文本替换每个匹配的元素

    * .html()
    * .text()

5. 移除每个匹配元素中的元素

    * .empty()

6. 从文档中移除每个匹配元素及其后代元素，但不实际删除它们

    * .remove()


## AJAX 数据格式

AJAX 支持多种数据格式，就目前的网络发展状态来看得话，JSON 和 XML 比较流行，而由于目前 Web Service 的兴起，使得 JSON 这种格式得到了广泛的应用，因为它比 XML 更加简洁。

虽然 JSON 比较简洁易懂，也可以使用 jQuery 的 eval() 函数来解释，但需要注意的是 JSON 数据需要小心的构建，如果数据内包含有一些无法识别的和特殊的字符来说， javascript 可能无法解释成功，会导致页面上不会显示任何的内容，以现在的浏览器来说也不会报错。

当然，要使用 AJAX 现在有很多第三方的库来简化使用，但这需要你使用的具体的开发环境来选择，而且，根据你应用的 AJAX 的多少来决定使用轻量级还是重量级的套件。当然，也可以使用一些前端的 javascript 的框架来增强应用的可交互性，比如使用 embar.js 。

## 总结

尽管 jQuery 的 AJAX 功能非常的强大，但我们仍然可以使用第三方插件来让它变得更加的容易操作。
