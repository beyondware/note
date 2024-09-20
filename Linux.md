## root 修改密码

1、切换到 root 账号

```sh
sudo su
```

2、修改 root 密码

```sh
passwd root
```

## 免输密码

1、切换到 root 账号

```sh
sudo -i 提示符为“#”，不需要每次输入密码
```

```sh
sudo su
```

或者

```sh
sudo su root
```

2、编辑 visudo

```sh
visudo
```

3、修改

```sh
%sudo ALL=(ALL:ALL) ALL
```

修改为

```sh
%sudo ALL=(ALL:ALL) NOPASSWD:ALL
```

## 用户

### 添加用户

1、添加用户

```sh
useradd -m -g users -G wheel -s /bin/bash 用户名
```

2、修改用户密码

```sh
passwd 用户名
```

### 用户添加 sudo 权限

1、查看当前用户权限

```sh
sudo -l -U 用户名
```

2、将用户添加到 sudoers 组

#### 方法一

```sh
usermod -aG sudo 用户名
```

#### 方法二

```sh
sudo vim /etc/sudoers
```

添加

```sh
用户名   ALL=(ALL:ALL) ALL
```

3、验证结果

```sh
sudo -l -U 用户名
```

### 修改用户组

```sh
usermod -g root 用户名
```

### 删除用户（主目录及其文件）

```sh
userdel -rf 用户名
```

## 登陆用户

1、查看当前所有登录用户

```sh
who
```

2、查询当前登录的用户

```sh
whoami
```

## 当前 shell

```sh
echo $0
```

或者

```sh
ps -p $$
```

## 删除 bash 历史记录

```sh
cat /dev/null > ~/.bash_history && history -c && exit
```

## 删除 zsh 历史记录

1、编辑用户配置文件

```sh
sudo vim ~/.zshrc
```

2、修改

```sh
#历史纪录文件
HISTFILE=~/.zsh_history

#历史纪录条数
HISTSIZE=10000

#终端退出后，保存的历史纪录条数（改成0）
SAVEHIST=0

## 每个终端，共享历史记录
setopt share_history
```

3、刷新

```sh
source ~/.zshrc
```

## UEFI 还是 BIOS

```sh
ls /sys/firmware/efi/
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

## WiFi

### 查看 WiFi 状态

```sh
nmcli radio
```

1、开启 WiFi

```sh
nmcli radio wifi on
```

2、关闭 WiFi

```sh
nmcli radio wifi off
```

### WiFi 网络状态

```sh
sudo nmcli networking
```

> enabled  ##确认状态

```sh
sudo nmcli networking on  ##开启
```

### nmtui

```sh 
sudo nmtui
```

选择：Activate a connection（启用连接）

### nmcli

```sh
nmcli
```

```sh
sudo nmcli dev wifi list
```

```sh
sudo nmcli --ask dev wifi con
```

输入 SSID名称 和 SSID密码

```sh
nmcli  ## 确认状态
```

### wpa_supplicant

```sh
sudo iwlist wlan0 scan | grep SSID
```

```sh
sudo wpa_passphrase SSID名称 SSID密码
```

写入到配置文件

```sh
sudo wpa_passphrase SSID名称 SSID密码 > /etc/wpa_supplicant.conf
```

```sh
sudo vim /etc/wpa_supplicant.conf    ##删除掉带#psk这行
```

2、查看当前无线网卡信息

```sh
iwconfig
```

> iwconfig: command not found

```sh
sudo apt install wireless-tools
```

3、安装 USB 无线网卡固件

```sh
sudo apt install linux-firmware
```

> 通常情况，WiFi 芯片固件存放在 /lib/firmware 目录下

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
lspci | grep Network 或者简化 lspci | grep -i net
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

## 别名（alias）

### 全局配置

1、查看 bash 配置文件

```sh
ls /etc | grep bash
```

2、编辑 bash 配置文件

```sh
sudo vim /etc/bashrc
```

可能是 

```sh
sudo vim /etc/bash.bashrc
```

3、添加别名（注意：单引号）

```sh
alias ll='ls -alh'
```

### 用户配置

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

### 查看别名

```sh
alias
```

### 删除全部别名

```sh
unalias -a
```

### 设置专门的别名文件

```sh
sudo vim ~/.bash_aliases
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
