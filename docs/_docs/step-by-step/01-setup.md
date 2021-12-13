---
layout: step
title: 安装
menu_name: 手把手教程
position: 1
---
欢迎使用 Jekyll 手把手教程。本教程将帮助您从一些基本前端开发经验到能够构建第一个 Jekyll 站点（不依赖 GEM 主题版式）。

## 安装

Jekyll 是一个 Ruby 的 Gem。首先，在计算机上安装 Ruby。查阅[安装]({{ '/docs/installation/' | relative_url }})说明根据您的操作系统进行相关操作。

安装完 Ruby，再从终端安装 Jekyll：

```sh
gem install jekyll bundler
```

创建新 `Gemfile` 文件（用于解决项目依赖软件）：

```sh
bundle init
```

在文本编辑器中编辑 `Gemfile`，添加 jekyll：

```ruby
gem "jekyll"
```

运行 `bundle` 安装 jekyll。

现在您可以为本教程学到的所有 jekyll 命令添加 `bundle exec` 前缀，这样就可以
确保使用的版本与 `Gemfile` 中设置的一致了。

## 创建站点

是时候该创建一个站点了！为您的站点创建一个新目录，目录名您可以随意设定。教
程接下来的部分我们就称这个目录为 **root** 了。

您也可以将其初始化为一个 Git 仓库。

Jekyll 一大特点就是不需要数据库。所有内容和站点结构都是由可使用 Git 版本控制的文件。使用版本控制虽为可选但是推荐。您要学习更多关于 Git 的知识可以参阅 [Git 手册](https://guides.github.com/introduction/git-handbook/)。

来添加第一个文件吧。在 **root** 文件夹内创建 `index.html`，内容如下：

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>首页</title>
  </head>
  <body>
    <h1>Hello World!</h1>
  </body>
</html>
```

## 构建

因为 Jekyll 是一个静态站点生成程序，所以在它构建出站点之前我们是看不到站点的。运行下面任一命令来构建站点：

* `jekyll build` - 构建站点，在 `_site` 输出静态站点。
* `jekyll serve` - 做 `jekyll build` 同样的事，然后运行可访问本地服务器，可
在 `http://localhost:4000` 查看，在任何您修改数据后都可以重构站点。

{: .note .info}
当您开发站点时，使用 `jekyll serve`。如果想要对于每次内容修改需要强制刷新浏览器，可以使用 `jekyll serve --livereload`。
如果有冲突或者想要在 Jekyll 的开发站点使用不同的 URL，使用 `--host` 和 `--port` 参数可调整（参阅[服务命令选项]({{ '/docs/configuration/options/#serve-command-options' | relative_url }})）。

{: .note .warning}
用 `jekyll serve` 构建站点的 `_site` 不适合部署使用。用 `jekyll serve` 生成的站点链接和资产 URL 都是用 `https://localhost:4000` 或者相关的命令行设置值，而非[您的站点配置文件]({{ '/docs/configuration/' | relative_url }})中的值。学
习更多站点部署知识，阅读本教程的[部署]({{ '/docs/step-by-step/10-deployment/' | relative_url }})部分。


运行 `jekyll serve` 然后在浏览器中进入
<a href="http://localhost:4000" target="_blank" data-proofer-ignore>http://localhost:4000</a>。您会看到 "Hello World!"。

这时您可能会想，“就这？”。Jekyll 不过就是把 HTML 文件从一个地方复制到另一个地方吗？

冷静！少年。要学的东西还很多！

接下来，您会学到 Liquid 和模板知识。
