---
title: 页面
permalink: /docs/pages/
---

页面是内容的基本构成部分。这对于对立内容很好用（内容不关联日期或者不属于整
体内容的一部分，例如成员或者菜谱）。

添加页面最简单的方式就是在根目录添加起了合适文件名的 HTML 文件。也可以使用
Markdown 格式添加内容，然后保存为 `.md` 扩展名文件（系统会将其转换为 HTML 文
件）。一般站点都会有一个主页，一个关于页面，一个联系页面，根目录和对应的 URL
看起来应该是：

```
.
├── about.md    # => http://example.com/about.html
├── index.html    # => http://example.com/
└── contact.html  # => http://example.com/contact.html
```

如果有很多页面，可以使用文件夹进行组织。项目内源文件夹结构会原封不动的在编译
后的 `_site` 中出现。然而，如果一个页面有*不同*的前置参数 `permalink` 设置，
`_site` 中的子文件夹会相应改变。

```
.
├── about.md          # => http://example.com/about.html
├── documentation     # folder containing pages
│   └── doc1.md       # => http://example.com/documentation/doc1.html
├── design            # folder containing pages
│   └── draft.md      # => http://example.com/design/draft.html
```

## 修改输出 URL

也许您在编译时想要一个不同于源文件夹结构的输出形式。使用 [永久链接](/docs/permalinks/ "permalink") 就可以完全控制 URL 输出。

## 页面内容摘要

从 Jekyll 4.1.1 开始，可以在配置文件中通过设置 `page_excerpts` 为 `true` 来*选择*生成页面摘要。
