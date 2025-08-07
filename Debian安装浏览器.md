# Firefox

1、查看

```sh
apt list --installed | grep firefox
```

三个关联包：firefox、firefox-locale-en、firefox-locale-zh-hans

2、删除

```sh
sudo dpkg -P firefox firefox-locale-en firefox-locale-zh-hans
```

# LibreWolf

extrepo：用于 Ubuntu 和其他基于 Debian 系统，简化和管理外部软件源的添加和更新

```sh
sudo apt update && sudo apt install extrepo -y
```

```sh
sudo extrepo search | grep Found
```

```sh
sudo extrepo enable librewolf
```

```sh
sudo apt update && sudo apt install librewolf -y
```

## 参考

> https://librewolf.net/installation/debian/

# Chromium

1、安装

```sh
sudo apt install chromium-browser
```

2、删除

```sh
sudo apt remove chromium-browser
```
