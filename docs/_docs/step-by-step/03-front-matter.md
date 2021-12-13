---
layout: step
title: 前置参数
position: 3
---
前置参数是一段 [YAML](http://yaml.org/) 代码片段，通常置于文件开始处的两段三
连接线之间。

您可以使用前置参数设置页面变量：

```yaml
---
my_number: 5
---
```

您可以使用 `page` 变量在 Liquid 中调用前置变量。
例如，输出上面 `my_number` 变量的值：

{% raw %}
```liquid
{{ page.my_number }}
```
{% endraw %}

## 使用前置变量

使用前置变量改变站点的 `<title>`：

{% raw %}
```liquid
---
title: Home
---
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>{{ page.title }}</title>
  </head>
  <body>
    <h1>{{ "Hello World!" | downcase }}</h1>
  </body>
</html>
```
{% endraw %}

{: .note .info }
要使 Jekyll 处理页面的任何 Liquid tag 都 _必须_ 包含前置参数。

使 Jekyll 处理在前置参数中没有定义变量的页面，也需要三连线：

```yaml
---
---
```

接下来，您将学到关于布局和使用源码多于 HTML 的原因。
