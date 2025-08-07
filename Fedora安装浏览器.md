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
