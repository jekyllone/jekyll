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

A `Gemfile` is a list of gems used by your site. Every Jekyll site has a Gemfile in the main folder. 

For a simple Jekyll site it might look something like this:

```ruby
source "https://rubygems.org"

gem "jekyll"

group :jekyll_plugins do
  gem "jekyll-feed"
  gem "jekyll-seo-tag"
end
```

## Bundler

[Bundler](https://rubygems.org/gems/bundler) is a gem that installs all gems in your `Gemfile`. 

While you don't have to use `Gemfile` and `bundler`, it is highly recommended as it ensures you're running the same version of Jekyll and its plugins across different environments.

Install Bundler using `gem install bundler`. You only need to install it once, not every time you create a new Jekyll project. 

To install gems in your Gemfile using Bundler, run the following in the directory that has the Gemfile:

```
bundle install
bundle exec jekyll serve
```

To bypass Bundler if you aren't using a Gemfile, run `jekyll serve`.

See [Using Jekyll with Bundler](/tutorials/using-jekyll-with-bundler/) for more information about Bundler in Jekyll and for instructions to get up and running quickly.
