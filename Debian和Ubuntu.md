## 优化桌面

```sh
sudo apt install gnome-tweaks
```

```sh
sudo apt install gnome-shell-extensions
```

```sh
sudo apt install gnome-shell-extension-dashtodock
```

## open-vm-tools

1、安装

```sh
sudo apt install open-vm-tools open-vm-tools-desktop
```

2、无法复制和粘贴

```sh
vmware-user
```

3、警告

```sh
(vmware-user:2932): Gtk-WARNING **: 15:26:01.197: gtk_disable_setlocale() must be called before gtk_init()
```

解决方法：

```sh
sudo vim /usr/share/gnome/autostart/vmware-user.desktop
```

添加

```sh
[Desktop Entry]
Type=Application
Name=VMware User Agent
Exec=vmware-user
Icon=system-run
Comment=VMware User Agent
X-GNOME-Autostart-enabled=true
```

## 镜像源

### Debian

1、遇到无法拉取 HTTPS 源

```sh
sudo apt install apt-transport-https ca-certificates
```

2、编辑

```sh
sudo vim /etc/apt/sources.list
```

3、修改

#### debian

> https://help.mirrors.cernet.edu.cn/debian/

```sh
http://deb.debian.org/debian
```

修改为

```sh
https://mirrors.cernet.edu.cn/debian/
```

#### debian-security

> https://help.mirrors.cernet.edu.cn/debian-security/

> https://mirrors.ustc.edu.cn/help/debian-security.html

```sh
http://security.debian.org/debian-security 或者 http://deb.debian.org/debian-security
```

修改为

```sh
https://mirrors.cernet.edu.cn/debian-security/
```

#### debian-ports（只适合 Debian riscv64）

> https://mirror.sjtu.edu.cn/docs/debian-ports

#### deb-multimedia

> https://deb-multimedia.org/

> https://help.mirrors.cernet.edu.cn/deb-multimedia/

- 官方源

```sh
deb https://www.deb-multimedia.org bookworm main non-free
```

- 镜像源

```sh
deb https://mirrors.cernet.edu.cn/deb-multimedia/ bookworm main non-free
```

4、更新

```sh
sudo apt update
```

### Deepin

1、编辑

```sh
sudo vim /etc/apt/sources.list
```

2、官方源

```sh
https://community-packages.deepin.com/deepin/
```

修改为

```sh
https://mirrors.nju.edu.cn/deepin/
https://mirrors.aliyun.com/deepin/
https://mirrors.tuna.tsinghua.edu.cn/deepin/
```

3、更新

```sh
sudo apt update
```

4、参考

> https://developer.aliyun.com/mirror/deepin

### Kali

1、编辑

```sh
sudo vim /etc/apt/sources.list
```

2、官方源

```sh
http://http.kali.org/kali
```

修改为

```sh
https://mirrors.cernet.edu.cn/kali
```

3、更新

```sh
sudo apt update
```

4、参考

> https://help.mirrors.cernet.edu.cn/kali/

> https://mirrors.ustc.edu.cn/help/kali.html

### Parrot

#### 安装卡住91%报错

> 命令 /usr/sbin/sources-media-unmount 未能在 600 秒内完成

- 安装前，修改

```sh
sudo vim /usr/sbin/sources-media-unmount
```

- 注释掉

```sh
# rm $CHROOT/etc/apt/sources.list || true
# mv $CHROOT/etc/apt/sources.list.orig $CHROOT/etc/apt/sources.list
# mv $CHROOT/etc/apt/sources.list.parrot $CHROOT/etc/apt/sources.list.d/parrot.list
```

1、编辑

```sh
sudo vim /etc/apt/sources.list.d/parrot.list
```

2、官方源

```sh
https://deb.parrot.sh/parrot/
```

修改为

```sh
https://mirrors.aliyun.com/parrot/
https://mirrors.ustc.edu.cn/parrot/
https://mirrors.tuna.tsinghua.edu.cn/parrot/
https://mirrors.sjtug.sjtu.edu.cn/parrot/
```

3、更新

```sh
sudo apt update
```

4、参考

> https://mirrors.sjtug.sjtu.edu.cn/docs/parrot

### Ubuntu

1、编辑

```sh
sudo vim /etc/apt/sources.list
```

2、官方源

#### ubuntu

```sh
http://archive.ubuntu.com/ubuntu/
```

修改为

```sh
https://mirrors.cernet.edu.cn/ubuntu/
```

> https://help.mirrors.cernet.edu.cn/ubuntu/

> https://mirrors.tuna.tsinghua.edu.cn/help/ubuntu/

#### ubuntu-ports

```sh
http://ports.ubuntu.com/
```

修改为

```sh
https://mirrors.cernet.edu.cn/ubuntu-ports/
```

> https://help.mirrors.cernet.edu.cn/ubuntu-ports/

> https://mirrors.tuna.tsinghua.edu.cn/help/ubuntu-ports/

#### ubuntu-old-releases（旧版本）

```sh
https://old-releases.ubuntu.com/ubuntu/
```

修改为

```sh
https://mirrors.cernet.edu.cn/ubuntu-old-releases/ubuntu/
```

> https://help.mirrors.cernet.edu.cn/ubuntu-old-releases/

#### ubuntu-security（未提供镜像）

> http://security.ubuntu.com/ubuntu/

3、更新

```sh
sudo apt update
```

### Linux Lite

#### ubuntu

1、编辑

```sh
sudo vim /etc/apt/sources.list
```

2、官方源

```sh
http://archive.ubuntu.com/ubuntu/
```

修改为

```sh
https://mirrors.cernet.edu.cn/ubuntu/
```

3、更新

```sh
sudo apt update
```

#### linuxlite

1、编辑

```sh
sudo vim /etc/apt/sources.list.d/linuxlite.list
```

2、官方源

```sh
http://repo.linuxliteos.com/linuxlite/
```

修改为

```sh
https://mirrors.sjtug.sjtu.edu.cn/linuxliteos/
```

3、更新

```sh
sudo apt update
```

### Linux Mint

1、编辑

```sh
sudo vim /etc/apt/sources.list.d/official-package-repositories.list
```

2、官方源

#### linuxmint

```sh
http://packages.linuxmint.com/
```

修改为

```sh
https://mirrors.cernet.edu.cn/linuxmint/
```

#### ubuntu

```sh
http://archive.ubuntu.com/ubuntu
```

修改为

```sh
https://mirrors.cernet.edu.cn/ubuntu/
```

3、更新

```sh
sudo apt update
```

4、参考

> https://help.mirrors.cernet.edu.cn/linuxmint/

### KDE neon

#### ubuntu

1、编辑

```sh
sudo vim /etc/apt/sources.list
```

2、官方源

```sh
http://archive.ubuntu.com/ubuntu/
```

修改为

```sh
https://mirrors.cernet.edu.cn/ubuntu/
```

3、更新

```sh
sudo apt update
```

#### neon

1、编辑

```sh
sudo vim /etc/apt/sources.list.d/neon.list
```

2、官方源

```sh
http://archive.neon.kde.org/user
```

修改为（好像镜像有问题）

```sh
https://mirrors.bfsu.edu.cn/kde-neon/user
https://mirror.nju.edu.cn/kde-neon/user
https://mirror.iscas.ac.cn/kde-neon/user
```

3、更新

```sh
sudo apt update
```

### openKylin

1、编辑

```sh
sudo vim /etc/apt/sources.list
```

2、官方源

```sh
https://archive.openkylin.top/openkylin/
```

修改为

```sh
https://mirror.nju.edu.cn/openkylin/
https://mirrors.lzu.edu.cn/openkylin/
```

3、更新

```sh
sudo apt update
```

## PPA

1、列出已安装 PPA

```sh
ls /etc/apt/sources.list.d/
```
2、删除 PPA

```sh
sudo add-apt-repository --remove ppa:username/ppa-name
```

```sh
sudo add-apt-repository --remove xxx.list
```

3、使用 PPA-Purge 删除 PPA

```sh
sudo apt install ppa-purge
```

```sh
sudo ppa-purge ppa:username/ppa-name
```

## 将 Ubuntu 22.04 升级到 Ubuntu 23.04

1、查看当前版本

```sh
lsb_release -a
```

2、系统更新并升级

```sh
sudo apt update && sudo apt upgrade
```

3、安装 update-manager-core

```sh
sudo apt install update-manager-core
```

开发版

```sh
update-manager -c -d
```

4、编辑

```sh
sudo vim /etc/update-manager/release-upgrades
```

> Prompt=lts

改为

> Prompt=normal

5、替代

```sh
sudo sed -i ‘s/jammy/lunar/g’ /etc/apt/sources.list
```

说明：jammy为22.04版本代号，lunar为23.04版本代号。

6、更新并升级

```sh
sudo apt update && sudo apt upgrade
```

7、执行升级

```sh
sudo apt dist-upgrade
```

8、开始版本升级

```sh
sudo do-release-upgrade -d
```

> 第三方 PPA 和存储库在升级期间被禁用

9、重启

```sh
sudo reboot
```

10、确认版本，是否升级成功

```sh
cat /etc/os-release
```

## Zorin OS 系统升级

```sh
sudo apt install zorin-os-upgrader
```

- 如果没有任何升级选项，执行以下命令：

```sh
gsettings set com.zorin.desktop.upgrader show-test-upgrades true
```

## 浏览器

### Firefox

1、查看

```sh
dpkg -L | grep firefox
```

- 三个关联包：firefox、firefox-locale-en、firefox-locale-zh-hans

2、删除

```sh
sudo dpkg -P firefox firefox-locale-en firefox-locale-zh-hans
```

### Chromium

1、安装

```sh
sudo apt install chromium-browser
```

2、删除

```sh
sudo apt remove chromium-browser
```

### Chrome

1、下载

```sh
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
```

2、安装

```sh
sudo apt install google-chrome-stable_current_amd64.deb
```

3、删除下载包

```sh
rm google-chrome-stable_current_amd64.deb
```
