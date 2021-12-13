---
title: 在其他 Linux 上安装 Jekyll
permalink: /docs/installation/other-linux/
---

在其他 Linux 上的安装过程类似在 [Ubuntu](../ubuntu/) 上的安装过程。

## 安装预装软件

### Fedora

```sh
sudo dnf install ruby ruby-devel openssl-devel redhat-rpm-config @development-tools
```
### RHEL8/CentOS8

```sh
sudo dnf install ruby ruby-devel
sudo dnf group install "Development Tools"
```

### Debian

```sh
sudo apt-get install ruby-full build-essential
```

### Gentoo

```sh
sudo emerge -av jekyll
```

or

```sh
sudo emerge --ask --verbose jekyll
```

### ArchLinux

```sh
sudo pacman -S ruby base-devel
```

### OpenSUSE

```sh
sudo zypper install -t pattern devel_ruby devel_C_C++
sudo zypper install ruby-devel
```

### Clear Linux

```sh
sudo swupd bundle-add ruby-basic
```
## 安装 Jekyll

安装过程同 [Ubuntu](../ubuntu/)。
