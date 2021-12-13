---
title: 快速开始
permalink: /docs/
redirect_from:
  - /docs/home/
  - /docs/quickstart/
  - /docs/extras/
---
Jekyll 是一款静态站点生成程序——您只需用自己喜欢的标记语言书写内容和布局框架，Jekyll 会将其转换为静态网站。当然，您可以随意修改网站的样式、感觉、URL和页面数据等。

## 预装软件

Jekyll 需要：

* Ruby **{{ site.data.ruby.min_version }}** 版本或更高
* RubyGems
* GCC 和 Make

查阅[需求]({{ '/docs/installation/#requirements' | relative_url }})获取指南和详细细节。

## 说明

1. 安装所有[预装软件]({{ '/docs/installation/' | relative_url }})。
2. 安装 jekyll 和 bundler [gem]({{ '/docs/ruby-101/#gems' | relative_url }})。
```sh
gem install jekyll bundler
```
3. 在 `./myblog` 创建新 Jekyll 站点。
```sh
jekyll new myblog
```
4. 进入新目录。
```sh
cd myblog
```
5. 构建站点，启用本地服务器。
```sh
bundle exec jekyll serve
```
6. 查看 [http://localhost:4000](http://localhost:4000){:target="_blank"}

{: .note .warning}
如果您使用 Ruby 3.0.0 版本或更高，第 5 步[可能出错](https://github.com/github/pages-gem/issues/752)。您可以通过添加 `webrick` 来修复： `bundle add webrick`

{: .note .info}
添加参数 `--livereload` 给 `serve` 就可以在数据更新时自动更新页面： `bundle exec jekyll serve --livereload`


如果这个过程中您遇到任何错误，您需要仔细检查一下您是否安装了所有[需求]({{ '/docs/installation/#requirements' | relative_url }})里提到的依赖软件。 
如果您还有问题，请查阅[故障排除]({{ '/docs/troubleshooting/#configuration-problems' | relative_url }})。

{: .note .info}
不同的操作系统安装方法不尽相同。查阅我们的[指南]({{ '/docs/installation/#guides' | relative_url }})获取基于不同操作系统的说明。
