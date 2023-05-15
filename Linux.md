## SSH

1、安装 SSH

> Unit sshd.service could not be found.

> sshd（Fedora）或者 ssh（Debian），具体情况而定。

### Debian

```sh
sudo apt install openssh-server
```

### Fedora

- 查看是否安装

```sh
rpm -qa | grep openssh-server
```

- 安装

```sh
sudo dnf install openssh-server

```

### 查看版本

```sh
ssh -V
```

2、查看 SSH

```sh
systemctl status sshd 或者 sudo /etc/init.d/ssh status 或者 service sshd status
```

> Active: active (running) 表示开启

> Active: inactive (dead) 表示关闭

3、启动 SSH

```sh
sudo systemctl start sshd 或者 sudo /etc/init.d/ssh start 或者 service sshd start
```

4、开机启动 SSH

```sh
sudo systemctl enable sshd 或者 sudo systemctl enable ssh
```

5、禁止开机启动 SSH

```sh
sudo systemctl disable sshd
```

6、停止 SSH

```sh
sudo systemctl stop sshd 或者 sudo /etc/init.d/ssh stop 或者 service sshd stop
```

7、重启 SSH

```sh
sudo systemctl restart sshd 或者 sudo /etc/init.d/ssh restart 或者 service sshd restart
```

### 允许 SSH 远程登陆

> Remote rejected opening a shell channel: Error: Not connected

```sh
sudo vim /etc/ssh/sshd_config
```

```sh
# PermitRootLogin prohibit-password
```

改成

```sh
PermitRootLogin yes
```

### 查看运行状态

```sh
ps -e | grep ssh
```

> 显示 00:00:00 sshd，ssh-server已经启动。

## 家目录

### 家目录中文改为英文

#### 方案一（推荐）

```sh
export LANG=en_US
```

```sh
xdg-user-dirs-gtk-update
```

> 勾选：不要再次询问我（Don't ask me this again）

> 点击：更新名称（Update Names）

#### 方案二

1、先将中文目录对应重命名为英文

```sh
桌面：Desktop
下载：Downloads
模板：Templates
公共：Public
文档：Documents
音乐：Music
图片：Pictures
视频：Videos
```

2、修改配置

```sh
sudo vim ~/.config/user-dirs.dirs
```

```sh
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
```

3、重启生效

### 家目录英文改为中文

```sh
export LANG=zh_CN.UTF-8
```

```sh
xdg-user-dirs-gtk-update
```

## 快捷键打开 gnome-terminal

- 设置-键盘-自定义快捷键

```sh
名称：open in terminal
命令：/usr/bin/gnome-terminal
快捷键：Ctrl+Alt+T
```

## Linux 内核版本

```sh
uname -a
```

```sh
hostnamectl | grep -i kernel
```

- 显示的信息更详细

```sh
cat /proc/version
```

## WiFi 驱动

1、判断网卡是否免驱

```sh
ifconfig -a
```

> 查看是否有wlan0、eth1、usb0开头的信息

2、查看当前无线网卡信息

```sh
iwconfig
```

- 出现 iwconfig: command not found

```sh
sudo apt install wireless-tools
```

3、安装 USB 无线网卡固件

```sh
sudo apt install linux-firmware
```

> 通常情况下, WiFi芯片固件存放在/lib/firmware目录

4、PCI 无线网卡

```sh
sudo apt install pciutils
```

- 查看网卡信息

```sh
lspci
```

- 过滤干扰信息

```sh
lspci | grep Network 或者 lspci | grep -i net
```

5、USB 无线网卡

```sh
sudo apt install usbutils
```

- 查看网卡信息

```sh
lsusb
```

6、BCM 无线网卡

```sh
dmesg | grep brcm
```

7、编译网卡驱动

```sh
sudo apt install linux-headers-$(uname -r)
```

> 编译需要 git、gcc、make、autoconf、build-essential 等依赖

8、查看驱动加载报错信息

```sh
dmesg
```

## 查看 WiFi 状态

```sh
nmcli radio
```

### 开启 WiFi

```sh
nmcli radio wifi on
```

### 关闭 WiFi

```sh
nmcli radio wifi off
```

## 解压缩

```sh
tar -zxvf 下载包.tar.gz
```

```sh
tar -jxvf 下载包.tar.bz2
```

```sh
tar -Jxvf 下载包.tar.xz
```

## 中文输入法

### ibus

1、安装

```sh
sudo apt install ibus ibus-libpinyin
```

2、编辑

```sh
sudo vim ~/.bashrc
```

3、添加

```sh
export GTK_IM_MODULE=ibus
export XMODIFIERS=@im=ibus
export QT_IM_MODULE=ibus
```

4、刷新

```sh
source ~/.bashrc
```

> 注：可能重启才会生效。

5、ibus-setup

默认 "General"（常规）-选择 "Preferences"（首选项）-点击 "Input Methods"（输入法）-点击 "Add"（添加）————Chinese-Intelligent Pinyin

6、参考

> https://github.com/ibus/ibus/wiki

> https://wiki.archlinux.org/title/IBus

#### 若 ibus 尚未启动

1、编辑

```sh
sudo vim /etc/environment
```

2、添加

```sh
export GTK_IM_MODULE=ibus
export XMODIFIERS=@im=ibus
export QT_IM_MODULE=ibus
ibus-daemon -rxR
```

3、重启电脑

4、若还是无法输入中文

```sh
sudo apt install ibus-clutter ibus-gtk ibus-qt im-config
```

## 别名

### 全局用户

```sh
sudo vim /etc/bashrc
```
### 当前用户

1、编辑

```sh
sudo vim ~/.bashrc
```

2、添加别名（注意：单引号）

```sh
alias ll='ls -alh'
```

3、刷新

```sh
source ~/.bashrc
```

4、查看别名

```sh
alias
```

5、删除全部别名

```sh
unalias -a
```
