---
title: 博文
permalink: /docs/posts/
redirect_from:
  - /docs/drafts/
---

博客属性对于 Jekyll 而言可谓“与生俱来”。您只需负责编写博文，剩下的事情交给
 Jekyll。

## 博文文件夹

文件夹 `_posts` 是放置博文的地方。您可以编写 [Markdown](https://daringfireball.net/projects/markdown/) 格式或者 HTML 
格式的文章。

## 新建博文

新建博文，就是在 `_posts` 文件夹新建一个文件，文件名格式如下：

```
YEAR-MONTH-DAY-title.MARKUP
```

`YEAR` 是四位数，`MONTH` 和 `DAY` 是两位数，`MARKUP` 是文件扩展名（代表文件内
容使用的格式）。例如，下面都是有效的文件名：

```
2011-12-31-new-years-eve-is-awesome.md
2012-09-12-how-to-write-a-blog.md
```

所有博文必须以[前置参数](/docs/front-matter/ "front matter")开始，参数中可以
设置[布局](/docs/layouts/ "layout")或者其他元数据。简单参数设置如下：

```markdown
---
layout: post
title:  "Welcome to Jekyll!"
---

# Welcome

**Hello world**, this is my first Jekyll blog post.

I hope you like it!
```

<div class="note">
  <h5>专家提示™：链接到其他博文</h5>
  <p>
    使用 <a href="/docs/liquid/tags/#linking-to-posts"><code>post_url</code></a>
    标签链接到其他博文，则无需担心因为站点永久链接方式改变而导致的链接崩溃。
  </p>
</div>

<div class="note info">
  <h5>了解字符编码</h5>
  <p>
    内容处理器可以修改特定字符使它们看起来更好看一些。例如，Redcarpet 的
     <code>smart</code> 扩展库会将 ASCII 的引号转为 Unicode 中的更弯曲一些的
    引号。为了在浏览器中正确显示这些字符，需要在页面布局的 <code>&lt;head&gt;</code>
    部分包含 <code>&lt;meta charset=&quot;utf-8&quot;&gt;</code> 元数据设置。
  </p>
</div>

## 包含图像和资源

有时页面需要包含一些图像、下载或者其他一些跟内容相关的数字资源。常用做法就是
在根目录创建一个叫做 `assets` 的文件夹，把文件、图像和其他资源放置其中。然后，
从博文中使用根目录路径引用它们。最好的使用方式依赖站点域名和路径的配置，但是
在 Markdown 也可以使用简单的方式：

在一个博文中包含一个图像：

```markdown
... 下面显示截屏：
![我的有用的截屏](/assets/screenshot.jpg)
```

链接一个用于下载的 PDF 文件：

```markdown
... 您可以直接[获取 PDF](/assets/mydoc.pdf)。
```

## 显示博文索引

在另一个单独的页面创建博文索引得宜于
[Liquid](https://docs.shopify.com/themes/liquid/basics) 和它的标签。这是一个如
何创建您的博文链接清单的简单示例：

{% raw %}
```liquid
<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
```
{% endraw %}

您可以全方位控制（如何以及在哪儿）显示您的博文以及如何架构您的网站。如果您
需要更详细信息，可以查阅 Jekyll [模板如何工作](/docs/templates/)。

注意 `post` 变量仅在 `for` 循环体内存在。如果您要访问当前页面/博文变量（博
文/页面的 `for` 循环题内的变量），使用 `page` 变量。

## 标签和分类

Jekyll 对博文中的 *tags* 和 *categories* 标签提供一流支持。

### Tags

Tags 在博文的前置参数中定义：单独的关键词用 `tag`；多个关键词用 `tags`。
Jekyll 会映射 `tags` 到多个关键词，系统会自动以空格*分割*字符串。例如，前置
参数中 `tag: classic hollywood` 会自动认定为一个词组 `"classic hollywood"`，
而 `tags: classic hollywood` 会被处理为字符数组 `["classic", "hollywood"]`。

不管前置参数选择哪种方式，Jekyll 都会以单数形式存储映射用于 Liquid 模板调用。

当前站点的所有 Tag 通过 Liquid 模板语言的 `site.tags` 可以引用。通过页面的
 `site.tags` 可以循环输出两项内容，第一项是 Tag 名，第二项是使用该 Tag 的
*博文数组*。

{% raw %}
```liquid
{% for tag in site.tags %}
  <h3>{{ tag[0] }}</h3>
  <ul>
    {% for post in tag[1] %}
      <li><a href="{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
  </ul>
{% endfor %}
```
{% endraw %}


### Categories

Categories 使用方法同上面的 tags 相似：
  * 通过前置参数定义：`category` 或者 `categories` （逻辑同 tags）
  * 站点所有分类可通过 Liquid 模板的 `site.categories` 循环引用（循环同 tags）

*Categories 和 Tags 相似性到此为止。*

不像 Tags，Categories 也可以通过博文的文件路径定义。`_post` 下的任何目录都可
被看作分类。例如，如果一篇博文的路径是 `movies/horror/_posts/2019-05-21-bride-of-chucky.markdown`，
那么 `movies` 和 `horror` 会自动被认定为该篇博文的分类。

当博文在前置参数中定义分类后，如果已经有对应分类，则会加入相应列表内。

分类（category）和标签（tag）之间标志性的区别是分类下的博文可以并入对应
[URL 路径](/docs/permalinks/#global)，而标签（tag）却不能。

所以，不管前置参数是 `category: classic hollywood` 还是 `categories: classic hollywood`，上面的示例 URL 会是
`movies/horror/classic%20hollywood/2019/05/21/bride-of-chucky.html` 或
`movies/horror/classic/hollywood/2019/05/21/bride-of-chucky.html` 。


## 博文摘要

您可以通过使用 `excerpt` 变量访问博文的内容片段。默认片段为内容的第一段。当然，也可以在前置参数或者 `_config.yml` 中使用 `excerpt_separator` 变量定义。

```markdown
---
excerpt_separator: <!--more-->
---

Excerpt with multiple paragraphs

Here's another paragraph in the excerpt.
<!--more-->
Out-of-excerpt
```

这是一个输出带有摘要的博文列表示例：

{% raw %}
```liquid
<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
      {{ post.excerpt }}
    </li>
  {% endfor %}
</ul>
```
{% endraw %}

## 草稿

草稿是文件名中没有日期的博文——一般是还需要编辑或者不想发布的博文。使用草
稿功能需要在站点根目录创建 `_drafts` 文件夹，然后创建您的第一篇草稿：

```
.
├── _drafts
│   └── a-draft-post.md
...
```

预览站点草稿，运行 `jekyll serve` 或者 `jekyll build` 带上 `--drafts` 参数开关
即可。草稿显示时间都是草稿文件最后修改的日期和时间，所以您看到的就是该草稿
都是按照修改时间顺序显示的博文草稿。
