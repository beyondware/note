## 镜像源

### Debian

1、编辑

```sh
sudo vim /etc/apt/sources.list
```

2、官方源

```sh
http://deb.debian.org/debian
```

修改为

```sh
https://mirrors.cernet.edu.cn/debian/
```

3、更新

```sh
sudo apt update
```

4、参考

> https://help.mirrors.cernet.edu.cn/debian/

> https://mirrors.tuna.tsinghua.edu.cn/help/debian/

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

### Ubuntu

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

4、参考

> https://help.mirrors.cernet.edu.cn/ubuntu/

> https://mirrors.tuna.tsinghua.edu.cn/help/ubuntu/

> https://developer.aliyun.com/mirror/ubuntu

### Linux Mint

1、编辑

```sh
sudo vim /etc/apt/sources.list.d/official-package-repositories.list
```

2、修改

#### Linux-Mint

```sh
http://packages.linuxmint.com/
```

修改为

```sh
https://mirrors.cernet.edu.cn/linuxmint/
```

#### Ubuntu

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

```sh
https://help.mirrors.cernet.edu.cn/linuxmint/
```

### KDE neon

#### Ubuntu

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

#### KDE-neon

1、编辑

```sh
sudo vim /etc/apt/sources.list.d/neon.list
```

2、官方源

```sh
http://archive.neon.kde.org/user
```

修改为

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

## 将Ubuntu 22.04升级到Ubuntu 23.04

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

注：jammy为22.04版本，lunar为23.04版本

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
