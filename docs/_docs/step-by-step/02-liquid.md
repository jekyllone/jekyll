---
layout: step
title: Liquid
position: 2
---
Liquid 使 Jekyll 开始变得有趣了。它是一门包含三个主要组件的模板语言：
  * [object](#objects)
  * [tag](#tags) 
  * [filter](#filters)

## Object

Object 告知 Liquid 在页面中输出预定义[变量](../../variables/)内容。object 使用双花括号标识：{% raw %}`{{`{% endraw %} 和 {% raw %}`}}`{% endraw %}。 

例如：{% raw %}`{{ page.title }}`{% endraw %} 显示 `page.title` 变量。

## Tag

Tag 定义模板的逻辑和控制流。tags 用花括号和百分号标识：{% raw %}`{%`{% endraw %} 和 {% raw %}`%}`{% endraw %}。

例如：

{% raw %}
```liquid
{% if page.show_sidebar %}
  <div class="sidebar">
    sidebar content
  </div>
{% endif %}
```
{% endraw %}

这段代码表示如果页面变量 `show_sidebar` 的值为 `true` 时显示 sidebar 内容。 

学习更多 tags 知识查阅 Jekyll [这里](/docs/liquid/tags/)。

## Filter

Filter 会改变 Liquid 对象的输出。它们常使用 `|` 分割，用于输出。 

例如：

{% raw %}
```liquid
{{ "hi" | capitalize }}
```
{% endraw %}

这将会显示 `Hi` 而不是 `hi`。 

[学习更多 filter 知识](/docs/liquid/filters/)。

## 使用 Liquid

现在，用 Liquid 使您的来自[安装](../01-setup/)的 `Hello World!` 小写（lowercase）输出：

{% raw %}
```liquid
...
<h1>{{ "Hello World!" | downcase }}</h1>
...
```
{% endraw %}

在页面顶部添加[前置参数](../03-front-matter/)可使 Jekyll 处理您的修改：

```yaml
---
# 前置参数告诉 Jekyll 处理 Liquid
---
```

您的 HTML 文档看起来应该这样：

{% raw %}
```html
---
---

<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>首页</title>
  </head>
  <body>
    <h1>{{ "Hello World!" | downcase }}</h1>
  </body>
</html>
```
{% endraw %}

当您刷新浏览器时就会看到 `hello world!`。

Jekyll 的大部分威力都来自与 Liquid 的相关功能联合使用。在页面添加前置参数使 Jekyll 处理 Liquid 变量。

接下来，您会学习关于前置参数的相关知识。
