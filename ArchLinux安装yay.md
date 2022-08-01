### 安装依赖

```sh
sudo pacman -S base-devel git
```

### 安装 yay 稳定版

1、克隆 yay

```sh
sudo git clone https://aur.archlinux.org/yay.git
```

2、修改目录所有者

```sh
sudo chown -R 用户名:用户组 ./yay
```

- 不知道用户组，可以用以下命令查询

```sh
id 用户名
```

3、编译

```sh
cd yay
```

```sh
makepkg -si
```

4、不允许使用 root 账号

```sh
==> ERROR: Running makepkg as root is not allowed as it can cause permanent,
catastrophic damage to your system.
```

### yay 用法

1、安装

```sh
yay -S 软件名
```

2、删除

```sh
yay -Rns 软件名
```

3、系统升级

```sh
yay -Syu
```

4、获取系统信息

```sh
yay -Ps
```

5、搜索

```sh
yay -Ss
```

### 安装 pamac

```sh
yay -S pamac-aur
```

运行

```sh
pamac-manager
```
