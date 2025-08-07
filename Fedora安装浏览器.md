# Firefox

1、查看安装情况

```sh
dnf list installed | grep firefox
```

2、删除

```sh
sudo dnf autoremove firefox
```

# LibreWolf

1、添加存储库

```sh
sudo dnf config-manager --add-repo https://rpm.librewolf.net/librewolf-repo.repo
```

2、安装

```sh
sudo dnf install librewolf
```

3、启动

```sh
librewolf
```

4、删除

```sh
sudo dnf autoremove librewolf
```

5、删除存储库

① 切换到目录

```sh
cd /etc/yum.repos.d
```

② 删除

```sh
sudo rm librewolf-repo.repo
```

6、参考

> https://librewolf.net/installation/fedora/

> https://rpm.librewolf.net/

# Chromium

1、安装

```sh
sudo dnf install chromium
```

2、删除

```sh
sudo dnf autoremove chromium
```

# Microsoft Edge

1、导入GPG密钥

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
```

2、添加存储库

```sh
sudo dnf config-manager --add-repo https://packages.microsoft.com/yumrepos/edge
```

3、正式开始

## 稳定版（推荐）

① 安装

```sh
sudo dnf install microsoft-edge-stable
```

② 启动

```sh
microsoft-edge
```

③ 删除

```sh
sudo dnf autoremove microsoft-edge
```

## 测试版

① 安装

```sh
sudo dnf install microsoft-edge-beta
```
② 启动

```sh
microsoft-edge-beta
```

③ 删除

```sh
sudo dnf autoremove microsoft-edge-beta
```

## 开发版

① 安装

```sh
sudo dnf install microsoft-edge-dev
```
② 启动

```sh
microsoft-edge-dev
```

③ 删除

```sh
sudo dnf autoremove microsoft-edge-stable-dev
```

4、删除存储库

① 切换到目录

```sh
cd /etc/yum.repos.d
```

② 删除

```sh
sudo rm packages.microsoft.com_yumrepos_edge.repo microsoft-edge.repo
```

## 存储库

> https://packages.microsoft.com/yumrepos/edge/Packages/m/
