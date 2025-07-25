## tty

```sh
Ctrl+Alt+F2   ##命令行
Ctrl+Alt+F7   ##图形界面
```

## 切换到 root

```sh
sudo -i
或者
sudo su
或者
sudo su root
或者
su
或者
su -
或者
su root
```

### 切换到 root 失败

```sh
su root
```

su: 身份验证失败

```sh
sudo passwd root
```

安装系统时，root 密码未设置，所以需要设置 root 密码。

### 修改 root 密码

1、切换到 root 账号

```sh
sudo -i
```

2、修改 root 密码

```sh
passwd root
```

## 免输密码

1、切换到 root 账号

```sh
sudo -i  //提示符为“#”，不需要每次输入密码
```

2、编辑 visudo

```sh
visudo
```

将

```sh
%sudo ALL=(ALL:ALL) ALL
```

修改为

```sh
%sudo ALL=(ALL:ALL) NOPASSWD:ALL
```

## 查看当前 shell

```sh
echo $SHELL
或者
echo $0
或者
ps -p $$
```

### 修改 shell

1、查看系统中所有可用的 shell

```sh
cat /etc/shells
```

2、更改默认 shell

```sh
chsh -s /bin/bash
```

3、重启系统才会生效。

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

#终端退出后，保存的历史纪录条数（改成0，退出终端zsh历史记录清除）
SAVEHIST=0

## 每个终端，共享历史记录
setopt share_history
```

3、刷新

```sh
source ~/.zshrc
```

## 设置默认编辑器

```sh
sudo update-alternatives --config editor
```

选择 vim.basic

## UEFI 还是 BIOS

```sh
ls /sys/firmware/efi/
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

## 是否虚拟化

### lscpu

```sh
LC_ALL=C.UTF-8 lscpu | grep Virtualization
```

输出结果

```sh
Virtualization:        VT-x
```

### egrep

```sh
grep -E --color=auto 'vmx|svm|0xc0f' /proc/cpuinfo
```

输出结果

```sh
vmx（Intel-VT）或 svm（AMD-V）
```

### virt-host-validate

```sh
sudo dnf install libvirt-client
sudo virt-host-validate
```

```sh
sudo apt install libvirt-clients
sudo virt-host-validate
```

输出结果

```sh
QEMU: Checking for hardware virtualization        : PASS
```

### cpu-checker

```sh
sudo apt install cpu-checker
sudo kvm-ok
```

输出结果

```sh
INFO: /dev/kvm exists
KVM acceleration can be used
```

## 显卡类型

```sh
lspci | grep -e VGA -e 3D
```

## 系统架构

### 显示操作系统架构类型

```sh
arch
```

### 直接显示 Linux 系统架构

```sh
uname -m
```

```sh
lsb_release -a
```

### 提供更详细的 CPU 信息

```sh
lscpu
```

### 查询 Linux 内核版本

```sh
hostnamectl | grep -i kernel
```

### 是否 64 位操作系统

```sh
dpkg --print-architecture
```

### 显示详细信息

```sh
cat /proc/version
```

## timedatectl 时区

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

### nmtui（登陆 WiFi）

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

查看 PCI 网卡信息

```sh
lspci
```

过滤干扰信息

```sh
lspci | grep Network 或者简化 lspci | grep -i net
```

5、USB 无线网卡

```sh
sudo apt install usbutils
```

查看 USB 网卡信息

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
