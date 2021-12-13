---
title: 在 Ubuntu 上安装 Jekyll 
permalink: /docs/installation/ubuntu/
---

## 安装依赖软件

安装 Ruby 和其他[预装软件]({{ '/docs/installation/#requirements' | relative_url }})：

```sh
sudo apt-get install ruby-full build-essential zlib1g-dev
```

尽量不要用 `root` 用户身份安装 RubyGems（通常称为 gem）包，而是使用您的常用
用户账号目录来安装。配置 gem 安装路径可以用下面的命令添加环境变量到 `~/.bashrc` 文件：

```sh
echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

最后，安装 Jekyll 和 Bundler：

```sh
gem install jekyll bundler
```

完毕！您准备好开始您的 Jekyll 之旅了吗？
