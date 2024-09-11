## 对应按键

1、Windows

```sh
Windows 键
```

2、Linux

```sh
Super 键 或者 Meta 键
```

3、macOS

```sh
⌘（即：Command 键）
```

## tty2 - tty6 命令行终端

```sh
Ctrl+Alt+F2 - F6
```

## 重启系统，访问 BIOS

```sh
systemctl reboot --firmware-setup
```

## 删除 bash 历史记录并退出

```sh
cat /dev/null > ~/.bash_history && history -c && exit
```

## 清理 zsh 历史记录

1、查看 history 文件地址

```sh
echo $HISTFILE
```

2、执行以下命令

```sh
echo > ~/.zsh_history
```

3、退出终端，历史记录清除。

## UEFI 还是 BIOS

```sh
ls /sys/firmware/efi/
```

## Wayland 还是 X11

```sh
echo $XDG_SESSION_TYPE
```

## init 还是 systemd

```sh
ps -p 1
```

## 显卡类型

```sh
lspci | grep -e VGA -e 3D
```

## 是否支持虚拟化

```sh
LC_ALL=C lscpu | grep Virtualization
```

## 是否 64 位操作系统

```sh
dpkg --print-architecture
```

## 查看 Linux 内核版本

```sh
uname -a
```

```sh
hostnamectl | grep -i kernel
```

- 详细信息

```sh
cat /proc/version
```

## 切换到 root 账号

```sh
sudo su 或者 sudo su root
```

```sh
sudo -i 提示符为“#”，不需要每次输入密码
```

## visudo

### 不输入密码使用 sudo

```sh
sudo visudo
```

追加

```sh
用户名 ALL=(ALL) NOPASSWD:ALL
```

## 用户拥有 sudo 权限

- 查看当前用户权限

```sh
sudo -l -U 用户名
```

### 将用户添加到 sudoers 组

#### 方法一

```sh
usermod -aG sudo 用户名
```

#### 方法二

```sh
vim /etc/sudoers
```

- 添加

```sh
用户名    ALL=(ALL:ALL) ALL
```

### 验证,是否添加成功。

```sh
sudo -l -U 用户名
```

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

### Arch

```sh
sudo pacman -S openssh
```

2、查看 SSH 版本

```sh
ssh -V
```

3、查看 SSH

```sh
systemctl status ssh 或者 sudo /etc/init.d/ssh status 或者 service sshd status
```

> Active: active (running) 表示开启

> Active: inactive (dead) 表示关闭

4、启动 SSH

```sh
sudo systemctl start ssh 或者 sudo /etc/init.d/ssh start 或者 service sshd start
```

5、开机启动 SSH

```sh
sudo systemctl enable ssh
```

6、禁止开机启动 SSH

```sh
sudo systemctl disable ssh
```

7、停止 SSH

```sh
sudo systemctl stop ssh 或者 sudo /etc/init.d/ssh stop 或者 service sshd stop
```

8、重启 SSH

```sh
sudo systemctl restart ssh 或者 sudo /etc/init.d/ssh restart 或者 service sshd restart
```

## 允许 SSH 远程登陆

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

### 查看 ssh 进程

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

## 别名

### 全局用户

1、查看 bash 配置文件

```sh
ls /etc | grep bash
```

注：可能是 bashrc，也可能是 bash.bashrc 文件。

2、编辑 bash 配置文件

```sh
sudo vim /etc/bashrc 或者 sudo vim /etc/bash.bashrc（Debian）
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

专门设置别名的文件

```sh
~/.bash_aliases
```

## 时区

1、显示当前时区

```sh
timedatectl
```

2、列出有效时区

```sh
timedatectl list-timezones
```

3、设置时区

```sh
sudo timedatectl set-timezone Asia/Shanghai
```
