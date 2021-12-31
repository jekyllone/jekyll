---
title:  命令行用法
permalink: /docs/usage/
---

Jekyll 的 gem 包安装之后，`jekyll` 命令就可以在终端命令执行相关操作。

`jekyll` 命令行操作基本结构是：

```
jekyll command [argument] [option] [argument_to_option]

示例：
    jekyll new site/ --blank
    jekyll serve --config _alternative_config.yml
```

常用的是本地开发时使用 `jekyll serve` 运行本地站点和 `jekyll build` 生成产品
级网站。

全部选项和参数使用方法，参阅[编译命令选项](/docs/configuration/options/#build-command-options)。

常用命令如下：

* `jekyll new PATH` - 在指定路径创建使用默认主题的新 Jekyll 站点。站点包含默
认必需目录。
* `jekyll new PATH --blank` - 在指定路径创建新的 Jekyll 站点框架。
* `jekyll build` 或 `jekyll b` - 在 `./_site` 编译生成离线站点（默认值）。
* `jekyll serve` 或 `jekyll s` - 在本地运行站点，并且随时更新编译源文件。
* `jekyll clean` - 删除所有生成文件：目标文件夹、元数据文件、Sass 和 Jekyll 缓存文件。
* `jekyll help` - 显示帮助，子命令可选，例如 `jekyll help build`。
* `jekyll new-theme` - 创建新 Jekyll 主题版式框架。
* `jekyll doctor` - 输出任何所有弃用生命和配置问题。

要更改 Jekyll 默认编译方法可以查看[配置项](/docs/configuration/)。
