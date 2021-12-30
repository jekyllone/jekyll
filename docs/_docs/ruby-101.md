---
title: Ruby 基础
permalink: /docs/ruby-101/
---

Jekyll 基于 Ruby。如果您没有接触过 Ruby，那么本页面将帮助您学习一些基础知识。

## Gems

Gem 是可以导入到 Ruby 项目内使用的代码。Gem 都具有特定功能，可以在多个项目或者跟其他人分享。Gem 可以执行：

* 转换 Ruby 对象为 JSON
* 分页
* 利用 API 集成到其他项目，例如 GitHub

Jekyll 就是一个 Gem。很多 Jekyll [插件]({{ '/docs/plugins/' | relative_url }})也是 Gem，例如
[jekyll-feed](https://github.com/jekyll/jekyll-feed)，
[jekyll-seo-tag](https://github.com/jekyll/jekyll-seo-tag) 和
[jekyll-archives](https://github.com/jekyll/jekyll-archives)。

## Gemfile

一个 `Gemfile` 就是一个站点所需 gem 清单。每个 Jekyll 站点在主文件夹内有一个 Gemfile。

对于一个极简的 Jekyll 站点而言 Gemfile 看起来这样：

```ruby
source "https://rubygems.org"

gem "jekyll"

group :jekyll_plugins do
  gem "jekyll-feed"
  gem "jekyll-seo-tag"
end
```

## Bundler

[Bundler](https://rubygems.org/gems/bundler) 是一个可以帮助安装 `Gemfile` 中所有 gem 的 gem。 

虽然不是必须使用 `Gemfile` 和 `bundler`，但是必须保证您使用的 Jekyll 和插件在不同的环境下版本一致。

安装 Bundler 运行命令 `gem install bundler` 即可。安装只需一次即可，不是每次创建新 Jekyll 项目都要安装。

使用 Bundler 安装 Gemfile 中的 gem，在 Gemfile 目录下运行命令：

```
bundle install
bundle exec jekyll serve
```

如果不使用 Gemfile，则不必运行 Bundler 相关命令，直接运行 `jekyll serve`。

查看[通过 Bundler 使用 Jekyll](/tutorials/using-jekyll-with-bundler/) 获取更多关于 Jekyll 和 Bundler 信息，以便快速掌握。
