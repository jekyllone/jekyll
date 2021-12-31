---
title: 插件
permalink: /docs/plugins/
---

Jekyll 有一套可以通过钩子程序来为站点生成自定义内容的插件系统。您可以不用修
改 Jekyll 源文件就可以为站点运行自定义代码。

{: .note .info}
您可以在 `_config.yml` 添加指定插件到 `whitelist` 中，这样就可以在安全模式运
行使用该插件。

* [安装]({{ '/docs/plugins/installation/' | relative_url }}) - 如何安装插件
* [您的第一款插件]({{ '/docs/plugins/your-first-plugin/' | relative_url }}) - 如何
编写插件
* [生成器]({{ '/docs/plugins/generators/' | relative_url }}) - 创建站点附加内容
* [转换器]({{ '/docs/plugins/converters/' | relative_url }}) - 更换内容标记语言
* [命令行]({{ '/docs/plugins/commands/' | relative_url }}) - 扩展 `jekyll` 子命令
* [标签]({{ '/docs/plugins/tags/' | relative_url }}) - 创建 Liquid 自定义标签
* [过滤器]({{ '/docs/plugins/filters/' | relative_url }}) - 创建 Liquid 自定义过滤器
* [钩子]({{ '/docs/plugins/hooks/' | relative_url }}) - 精准控制扩展编译过程
