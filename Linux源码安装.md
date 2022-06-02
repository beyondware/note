---
title: Linux 源码安装
author: beyondware
categories:
  - [Linux]
---

## 下载

```sh
wget 下载链接
```

## 解包

```sh
tar -zxvf ./包
```

## 进入包目录

```sh
cd ./包目录
```

## 配置

- 执行 configure 指定安装路径

```sh
./configure --prefix=/usr/local/包名
```

- 正确执行后，包目录生成一个 Makefile 文件

> creating objs/Makefile //显示结果

## 缺少依赖

> 缺少 xxx library，报错

```sh
sudo dnf install xxx xxx-devel
```

## 报错清理

```sh
make clean
```

## 编译

```sh
make
```

## 安装

```sh
make install
```

## 启动

- 安装成功后，一般进入下面路径，来启动、停止等操作。

> /usr/local/包名/sbin

- 如果启动失败，需要关闭防火墙

```sh
systemctl stop firewalld.service
```

1、启动

```sh
./包名
```

2、停止

```sh
./包名 -s stop
```

3、重新加载

```sh
./包名 -s reload
```
