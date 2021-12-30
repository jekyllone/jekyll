---
title: 前置参数
permalink: /docs/front-matter/
redirect_from: /docs/frontmatter/index.html
---

Jekyll 会处理任何包含 [YAML](https://yaml.org/) 格式前置参数的文件。前置参数必须是文件中最先出现且被三横线包围的有效 YAML 。基本格式如下示例：

```yaml
---
layout: post
title: Blogging Like a Hacker
---
```

三横线之间，您可以设置预定义变量（参考下面展示）或者创建自定义变量。这些
变量可供文件后面的 Liquid 标签或者其他任何页面/博文的布局或模板进行引用。

<div class="note warning">
  <h5>UTF-8 字符编码警告</h5>
  <p>
    如果您使用 UTF-8 编码，确保文件中没有 <code>BOM</code> 字符存在，否
    则 Jekyll 可能崩溃。尤其是如果您在
    <a href="{{ '/docs/installation/windows/' | relative_url }}">Windows 上运行 Jekyll</a> 时要注意。
  </p>
</div>

<div class="note">
  <h5>前置参数变量可选</h5>
  <p>
    如果您想使用 <a href="{{ '/docs/variables/' | relative_url }}">Liquid 表天和变量</a>
    但不需要前置参数中的任何东西，可以留空！两端三横线之间即使什么都没有
    也可以告诉 Jekyll 要处理该文件。（这对于 CSS 和 RSS feed 文件来说很重要！）
  </p>
</div>

## 预定义全局变量

页面或博文的前置参数中可以设置很多全局变量。

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
      <th>变量</th>
      <th>简介</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <p><code>layout</code></p>
      </td>
      <td>
        <p>

          如设置则指定所用布局文件。指定布局文件无需文件扩展名。布局文件
          必须在 <code>_layouts</code> 文件夹内。

        </p>
        <ul>
          <li>
            设定 <code>null</code> 将不使用布局。如果文件是博文/文档且在<a href="{{ '/docs/configuration/front-matter-defaults/' | relative_url }}">默认前置参数</a>中已设置布局，则此设置会被覆盖。
          </li>
          <li>
            从 3.5.0 版开始，在博文/文档中使用 <code>none</code> 不管默认
            前置参数设置与否都会生成无布局文件。页面使用 <code>none</code>
            会导致 Jekyll 寻找叫做 "none" 的布局文件。
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>permalink</code></p>
      </td>
      <td>
        <p>

          如果您需要自行设定博文的个性 URL，而不使用站点默认样式（默认 <code>/year/month/day/title.html</code>），那么系统会最终使用您设定的样式。

        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>published</code></p>
      </td>
      <td>
        <p>
          如果您不想让某些博文在站点编译时公开发布，可以设置其为 <code>false</code>。
        </p>
      </td>
    </tr>
  </tbody>
</table>
</div>

<div class="note">
  <h5>渲染博文标记为未发布</h5>
  <p>
    预览未发布页面，运行 <code>jekyll serve</code> 或者 <code>jekyll build</code>
    附带参数 <code>--unpublished</code> 即可。Jekyll 针对博文还有一个更方便的<a href="{{ '/docs/posts/#drafts' | relative_url }}">草稿</a>功能。
  </p>
</div>

## 自定义变量

您还可以在前置参数中设定方便自己在 Liquid 中使用的自定义变量。例如您可以
设定变量 `food`，然后再页面中使用：

{% raw %}
```liquid
---
food: Pizza
---

<h1>{{ page.food }}</h1>
```
{% endraw %}

## 博文预定义变量

还有一些方便博文中使用的变量。

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
      <th>变量</th>
      <th>简介</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <p><code>date</code></p>
      </td>
      <td>
        <p>
          这里设定的日期会覆盖博文文件名中的日期。本项可用于纠正博文排列顺
          序。日期指定格式为 <code>YYYY-MM-DD HH:MM:SS +/-TTTT</code>，时、分、
          秒和时区为可选项。
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>category</code></p>
        <p><code>categories</code></p>
      </td>
      <td>
        <p>
          无需将博文放入文件夹，只要定义一个或多个博文所属分类即可。生成站点
          时就像博文设置了这些目录一样。分类可定义成 <a
          href="https://en.wikipedia.org/wiki/YAML#Basic_components">YAML 列表</a>或空格分开的字符串。
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>tags</code></p>
      </td>
      <td>
        <p>
          同分类一样，一篇博文可添加一个或多个 Tag。同分类相似，Tag 可定义为
           <a
          href="https://en.wikipedia.org/wiki/YAML#Basic_components">YAML 列表</a>或空格分割的字符串。
        </p>
      </td>
    </tr>
  </tbody>
</table>
</div>

<div class="note">
  <h5>DRY（不要自我重复）</h5>
  <p>
    如果不想不断重复高频前置参数变量，可以在
    <a href="{{ '/docs/configuration/front-matter-defaults/' | relative_url }}" title="Front Matter defaults">默认前置参数</a>中进行设定，必要时再进行覆盖（或者根本不需要）。这种设定在预置参数变量和自定义变量中都可以设定。
  </p>
</div>
