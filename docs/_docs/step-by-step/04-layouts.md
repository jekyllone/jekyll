---
layout: step
title: 布局
position: 4
---
Jekyll 构建页面时除了 HTML 也支持 [Markdown](https://daringfireball.net/projects/markdown/syntax)。对于内容结构相对简单（只有段落、标题和图像）的页
面而言，Markdown 是一个绝佳选择，因为使用 Markdown 绝对要比用 HTML 少写
很多代码。

在您的站点根文件夹下创建叫做 `about.md` 的新 Markdown 文件。

您可以复制 `index` 的内容并修改其为 About 页面内容。但是，这会创建重复的代码，必须为您添加到站点的每个新页面自定义这些代码。
this creates duplicate code that has to be customized for each new page you add
to your site. 

For example, adding a new stylesheet to your site would involve adding the link
to the stylesheet to the `<head>` of each page. For sites with many pages, this
is a waste of time.

## Creating a layout

Layouts are templates that can be used by any page in your site and wrap around page content.
They are stored in a directory called `_layouts`.

Create the `_layouts` directory in your site's root folder and create a new `default.html` file with the following content:

{% raw %}
```liquid
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>{{ page.title }}</title>
  </head>
  <body>
    {{ content }}
  </body>
</html>
```
{% endraw %}

This HTML is almost identical to `index.html` except there's
no front matter and the content of the page is replaced by a `content`
variable. 

`content` is a special variable that returns the rendered
content of the page on which it's called.

## Use layouts

To make `index.html` use your new layout, set the `layout` variable in the front
matter. The file should look like this:

{% raw %}
```liquid
---
layout: default
title: Home
---
<h1>{{ "Hello World!" | downcase }}</h1>
```
{% endraw %}

When you reload the site, the output remains the same.

Since the layout wraps around the content on the page, you can call front matter like `page` 
in the layout file. When you apply the layout to a page, it uses the front matter on that page.

## Build the About page

Add the following to `about.md` to use your new layout in the About page:

```markdown
---
layout: default
title: About
---
# About page

This page tells you a little bit about me.
```

Open <a href="http://localhost:4000/about.html" target="_blank" data-proofer-ignore>http://localhost:4000/about.html</a>
in your browser and view your new page.

Congratulations, you now have a two page website!

Next, you'll learn about navigating from page to page in your site. 
