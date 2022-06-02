---
title: 用Linux使用snap
author: beyondware
tags:
  - [snap]
categories:
  - [Linux]
---

## 安装环境

安装 snap 环境

- Ubuntu

```sh
sudo apt update
```

```sh
sudo apt install snapd
```

- Fedora

```sh
sudo dnf install shapd
```

安装 snap 商店(可选)

```sh
sudo snap install snap-store
```

## 常用命令

查找某一命令帮助

```sh
snap help 命令
```

查找要安装的软件

```sh
snap find 软件名
```

查找要安装的软件详细信息

```sh
snap info 软件名
```

列出已安装

```sh
snap list
```

下载某一软件包到电脑

```sh
snap download 软件名
```

安装

```sh
sudo snap install 软件名
```

卸载

```sh
sudo snap remove 软件名
```

更新

```sh
sudo snap refresh 软件名
```

运行

```sh
snap run 软件名
```

启用 snap

```sh
sudo snap enable
```

禁用 snap

```sh
sudo snap disable
```

指定目录打包成 snap

```sh
sudo snap pack
```

## 参考文档

> https://snapcraft.io/docs/installing-snapd

> https://snapcraft.io/store
