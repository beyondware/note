## 桌面右击无法打开终端

```sh
sudo apt install nautilus-open-terminal
```

## lxappearance

> https://github.com/lxde/lxappearance

```sh
sudo apt install lxappearance
```

## gnome-tweaks

```sh
sudo apt install gnome-tweaks
```

## Extension Manager

> https://github.com/mjakeman/extension-manager

```sh
sudo apt install gnome-shell-extension-manager
```

或者

```sh
sudo apt install gnome-shell-extensions
```

## Dash to Dock

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

```sh
sudo apt install deepin-unioncode
```

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

```sh
sudo apt update
```

```sh
sudo pkcon update
```

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

4、查看已添加的 GPG 密钥

```sh
sudo apt-key list
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

## Linux Mint 系统升级

- Linux Mint 安装指南

> https://linuxmint-installation-guide.readthedocs.io/en/latest/

- MintUpgrade

> https://github.com/linuxmint/mintupgrade

1、安装 MintUpgrade

```sh
sudo apt install mintupgrade
```

2、运行 MintUpgrade

```sh
sudo mintupgrade
```

## 浏览器

### Firefox

1、查看

```sh
apt list --installed | grep firefox
```

- 三个关联包：firefox、firefox-locale-en、firefox-locale-zh-hans

2、删除

```sh
sudo dpkg -P firefox firefox-locale-en firefox-locale-zh-hans
```

### LibreWolf

> https://librewolf.net/

1、更新系统

```sh
sudo apt update && sudo apt upgrade -y
```

2、安装所需的软件包

```sh
sudo apt install curl gnupg lsb-release apt-transport-https ca-certificates -y
```

3、导入 LibreWolf 存储库

```sh
curl https://deb.librewolf.net/keyring.gpg | gpg --dearmor \
    | sudo tee /usr/share/keyrings/librewolf.gpg >/dev/null
```

4、导入 GPG 密钥

```sh
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/librewolf.gpg] \
http://deb.librewolf.net $(lsb_release -sc) main" \
    | sudo tee /etc/apt/sources.list.d/librewolf.list
```

5、更新包列表

```sh
sudo apt update
```

6、安装 LibreWolf

```sh
sudo apt install librewolf -y
```

7、启动 LibreWolf

```sh
librewolf
```

8、删除 LibreWolf

```sh
sudo apt remove librewolf
```

9、删除 LibreWolf 存储库

```sh
sudo rm /etc/apt/sources.list.d/librewolf.list
```

10、删除 GPG 密钥

```sh
sudo rm /usr/share/keyrings/librewolf.gpg
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

### Microsoft Edge

> https://packages.microsoft.com/repos/edge/pool/main/m/microsoft-edge-stable/

1、更新系统

```sh
sudo apt update && sudo apt upgrade
```

2、安装所需的软件包

```sh
sudo apt install software-properties-common apt-transport-https curl ca-certificates -y
```

3、导入 Microsoft Edge APT 存储库

- 下载 GPG 密钥以验证包的真实性

```sh
curl -fSsL https://packages.microsoft.com/keys/microsoft.asc | sudo gpg --dearmor | sudo tee /usr/share/keyrings/microsoft-edge.gpg > /dev/null
```

- 将 Microsoft Edge 存储库添加系统中

```sh
echo 'deb [arch=amd64 signed-by=/usr/share/keyrings/microsoft-edge.gpg] https://packages.microsoft.com/repos/edge stable main' | sudo tee /etc/apt/sources.list.d/microsoft-edge.list
```

- 更新系统的存储库列表

```sh
sudo apt update
```

4、安装 Microsoft Edge 浏览器


#### 稳定版

```sh
sudo apt install microsoft-edge-stable
```

```sh
sudo apt upgrade microsoft-edge-stable
```

```sh
sudo apt remove microsoft-edge-stable
```

```sh
microsoft-edge -version
```

#### Beta 版

```sh
sudo apt install microsoft-edge-beta
```

```sh
sudo apt upgrade microsoft-edge-beta
```

```sh
sudo apt remove microsoft-edge-beta
```

```sh
microsoft-edge-beta --version
```

#### Dev 版

```sh
sudo apt install microsoft-edge-dev
```

```sh
sudo apt upgrade microsoft-edge-dev
```

```sh
sudo apt remove microsoft-edge-stable-dev
```

```sh
microsoft-edge-dev --version
```

5、删除 Microsoft Edge 所有存储库

```sh
sudo rm -rf /etc/apt/sources.list.d/microsoft*
```

6、删除 Microsoft Edge 密钥

```sh
sudo rm -rf /etc/apt/trusted.gpg.d/microsoft*
sudo rm -rf /usr/share/keyrings/microsoft*
```

### Waterfox

> https://flathub.org/apps/net.waterfox.waterfox

1、安装

```sh
flatpak install flathub net.waterfox.waterfox
```

2、运行

```sh
flatpak run net.waterfox.waterfox
```

3、删除

```sh
flatpak uninstall --delete-data net.waterfox.waterfox
```
