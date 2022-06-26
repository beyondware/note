---
title: openEuler最小化安装GNOME
author: beyondware
tags:
  - [openEuler]
categories:
  - [Linux]
---

## 分区

```sh
swap 2GB（交换分区、通常设置电脑内存的2倍）
/boot 1GB
/boot/efi 300M
/ 剩余留给root
```

## 联网

1、系统联网（正常不用管）

```sh
vi /etc/sysconfig/network-scripts/ifcfg-ens33
```

- ONBOOT=no 改成 yes

2、远程 SSH 登陆（正常不用管）

```sh
vi /etc/ssh/sshd_config
```

- PermitRootLogin no 改成 yes

3、修改源

```sh
vi /etc/yum.repos.d/openEuler.repo
```

将

> http://repo.openeuler.org/

改成（可选镜像）

> https://repo.huaweicloud.com/openeuler/

> https://mirrors.nju.edu.cn/openeuler/

> https://mirrors.tuna.tsinghua.edu.cn/openeuler/

## 最小化

1、系统更新

```sh
sudo dnf update
```

2、安装中文字体（否则乱码）

- 文泉驿

```sh
sudo dnf install wqy-microhei-fonts wqy-zenhei-fonts
```

- 思源字体（选装）

```sh
sudo dnf install google-noto-sans-cjk-sc-fonts google-noto-serif-cjk-sc-fonts
```

3、安装 gdm

```sh
sudo dnf install gdm
```

4、开机启动 gdm

```sh
sudo systemctl enable gdm
```

5、图形化登录

```sh
sudo systemctl set-default graphical.target
```

6、重启

```sh
reboot
```

## 选装

1、文件管理器

```sh
sudo dnf install nautilus
```

2、终端

```sh
sudo dnf install gnome-terminal
```
