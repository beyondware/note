## 准备工作

### Arch 安装指南

> https://wiki.archlinux.org/title/Installation_guide

### VMware Workstation 设置

> 编辑虚拟机设置→选项-高级-固件类型，改成：UEFI

### 设置终端字体大小

```sh
setfont ter-132n
```

### 联网（ping通就忽略）

#### 有线网络

```sh
pacman -S dhcpcd
```

```sh
dhcpcd
```

#### 无线网络

> https://wiki.archlinux.org/title/Iwd

1、进入 iwd 环境

```sh
iwctl
```

2、列出网卡设备

```sh
device list
```

3、扫描网络（wlan0：无线网卡）

```sh
station wlan0 scan
```

4、列出扫描到的网络

```sh
station wlan0 get-networks
```

5、连接无线网络

```sh
station wlan0 connect WiFi-ID
```

6、退出 iwd 环境

```sh
exit
```

### ssh（默认：开启）

1、启动 ssh

```sh
systemctl start sshd
```

2、开机启动 ssh

```sh
systemctl enable sshd
```

3、查看 ssh 状态

```sh
systemctl status sshd
```

- active (running) 表示开启

4、查看 ssh 进程

```sh
ps -e | grep sshd
```

### 分区

#### 传统 BIOS

1、查看磁盘

```sh
fdisk -l
```

2、磁盘分区

```sh
cfdisk /dev/sda
```

3、选择：gpt

4、磁盘类型

```sh
/dev/sda1 1M BIOS boot
/dev/sda2 2G Linux swap
/dev/sda3 剩余 Linux filesystem
```

5、光标回到 Write，输入 yes，回到 Quit 回车退出。

> Syncing disks.

##### 挂载

1、查看磁盘信息

```sh
fdisk -l
```

2、swap 分区

```sh
mkswap /dev/sda2
```

```sh
swapon /dev/sda2
```

3、根目录

```sh
mkfs.ext4 /dev/sda3
```

必须先挂载根目录

```sh
mount /dev/sda3 /mnt
```

#### 先进 EFI

1、检查磁盘信息，确认磁盘名称

```sh
fdisk -l
```

2、分区

```sh
cfdisk /dev/sda
```

3、选择：gpt

4、对应类型

```sh
/dev/sda1 512M EFI System
/dev/sda2 2G Linux swap
/dev/sda3 剩余 Linux filesystem
```

5、光标回到 Write，输入 yes，Quit 退出。

> Syncing disks.

##### 挂载

1、查看磁盘信息

```sh
fdisk -l
```

2、EFI 分区

```sh
mkfs.fat -F32 /dev/sda1  或者  mkfs.vfat /dev/sda1
```

3、swap 分区

```sh
mkswap /dev/sda2
```

```sh
swapon /dev/sda2
```

4、根目录

```sh
mkfs.ext4 /dev/sda3
```

```sh
mkfs.xfs /dev/sda3  ##支持大文件
```

必须先挂载根目录

```sh
mount /dev/sda3 /mnt
```

### 更新系统时间

```sh
timedatectl set-ntp true
```

```sh
timedatectl status
```

### 镜像源

#### 自动获取

```sh
reflector --country China --age 72 --sort rate --protocol https --save /etc/pacman.d/mirrorlist
```

#### 手动修改

1、编辑

```sh
vim /etc/pacman.d/mirrorlist
```

2、添加镜像源

```sh
## China
Server = https://mirror.nju.edu.cn/archlinux/$repo/os/$arch
Server = https://mirrors.tuna.tsinghua.edu.cn/archlinux/$repo/os/$arch
Server = https://mirrors.ustc.edu.cn/archlinux/$repo/os/$arch
Server = https://mirrors.sjtug.sjtu.edu.cn/archlinux/$repo/os/$arch
```

3、更新缓存

```sh
pacman -Syyu
```

4、更新 GPG key

```sh
pacman -S archlinux-keyring
```

5、查看镜像源

```sh
cat /etc/pacman.d/mirrorlist
```

### 装机必备

```sh
pacstrap /mnt base base-devel linux linux-firmware
```

```sh
pacstrap /mnt bash-completion git wget vim
```

### fstab

1、生成 fstab 文件

```sh
genfstab -U /mnt >> /mnt/etc/fstab
```

2、查看 fstab 信息

```sh
cat /mnt/etc/fstab
```

### 设置 root 密码

```sh
passwd root
```

------------------------------------------------------------------------------------------------------------------------------------------------------

## 进入 chroot 环境

```sh
arch-chroot /mnt
```

### grub 引导

> https://wiki.archlinux.org/title/GRUB

#### 传统 BIOS 引导

1、安装 grub

```sh
pacman -S grub
```

2、grub-install（整块硬盘：sda）

```sh
grub-install --target=i386-pc /dev/sda
```

- 输出以下信息，表示成功。

```sh
Installing for i386-pc platform.
Installation finished. No error reported.
```

3、导出 grub 配置文件（非常重要）

```sh
grub-mkconfig -o /boot/grub/grub.cfg
```

- 如果没有执行上述步骤，重启将报错以下信息，无法进入系统。

```sh
Minimal BASH-like line editing is supported.For the first word.TAB 
lists possible command completions.Anywhere else TAB lists possible 
device or file completions.
```

##### 执行 grub-install 报错

```sh
Installing for i386-pc platform.
grub-install: warning: this GPT partition label contains no BIOS Boot Partition; embedding won't be possible.
grub-install: warning: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
grub-install: error: will not proceed with blocklists.
```

1、安装 parted

```sh
pacman -S parted
```

2、parted

```sh
parted /dev/sda set 1 bios_grub on
```

- 输出结果

```sh
nformation: You may need to update /etc/fstab.
```

3、打印结果

```sh
parted /dev/sda print
```

4、grub-install（整块硬盘：sda）

```sh
grub-install /dev/sda
```

- 输出以下信息，表示成功。

```sh
Installing for i386-pc platform.
Installation finished. No error reported.
```

5、导出 grub 配置文件

```sh
grub-mkconfig -o /boot/grub/grub.cfg
```

#### 先进 EFI 引导

1、查看磁盘信息

```sh
fdisk -l
```

2、挂载 EFI 分区

```sh
mkdir -p /mnt/efi
```

```sh
mount /dev/sda1 /mnt/efi
```

3、安装引导检测器

```sh
pacman -S os-prober
```

```sh
os-prober
```

4、安装多重引导启动器

```sh
pacman -S grub efibootmgr
```

5、grub-install

```sh
grub-install --target=x86_64-efi --efi-directory=/mnt/efi --bootloader-id=GRUB
```

- 输出以下信息，表示成功。

```sh
Installing for x86_64-efi platform.
Installation finished. No error reported.
```

6、生成 GRUB 配置文件（非常重要）

```sh
grub-mkconfig -o /boot/grub/grub.cfg
```

7、查看配置文件

```sh
cat /boot/grub/grub.cfg
```

### 更改时区

```sh
ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
```

或者

```sh
timedatectl set-timezone Asia/Shanghai
```

```sh
hwclock --systohc
```

### 文本编码

1、编辑

```sh
vim /etc/locale.gen
```

```sh
en_US.UTF-8 UTF-8   ##去掉前面#
```

2、生成 locale 信息

```sh
locale-gen
```

- 输出信息

```sh
Generating locales...
  en_US.UTF-8... done
Generation complete.
```

3、写入

```sh
echo LANG=en_US.UTF-8 >> /etc/locale.conf
```

### 主机名

```sh
echo arch > /etc/hostname
```

- 编辑

```sh
vim /etc/hosts
```

- 添加

```sh
127.0.0.1   localhost
::1         localhost
127.0.1.1   arch.localdomain arch
```

### CPU 微指令

#### Intel

```sh
pacman -S intel-ucode
```

#### AMD

```sh
pacman -S amd-ucode
```

### NetworkManager

> https://wiki.archlinux.org/title/Network_configuration

- 警告：必须先装，不然新系统无法联网

```sh
pacman -S networkmanager
```

- 选装

```sh
pacman -S network-connection-editor network-manager-applet networkmanager-openvpn
```

```sh
systemctl enable NetworkManager
```

### dhcpcd

```sh
pacman -S dhcpcd
```

```sh
systemctl enable dhcpcd
```

# 设置 root 密码

```sh
passwd root
```

警告：必须先设置，不然新系统无法登陆

——————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————

### 退出 chroot 环境

```sh
exit
```

### 卸载挂载点

```sh
umount -R /mnt
```

- 查看挂载状态

```sh
lsblk -l
```

### 系统重启

```sh
reboot
```
------------------------------------------------------------------------------------------------------------------------------------------------------

## 进入全新系统

### ssh 安装

1、安装 openssh

```sh
pacman -S openssh
```

2、开启 ssh

```sh
systemctl start sshd
```

3、开机启动 ssh

```sh
systemctl enable sshd
```

4、查看 ssh 状态

```sh
systemctl status sshd
```

5、查看 ssh 进程

```sh
ps -e | grep sshd
```

### 添加新用户

1、添加用户到 wheel 组

```sh
useradd -m -g users -G wheel -s /bin/bash pc
```

2、设置用户密码

```sh
passwd pc
```

3、切换到 root 删除用户及其任何文件

```sh
userdel -rf pc
```

### 普通用户使用 root 权限

方法一、推荐

```sh
EDITOR=vim visudo
```

方法二、不推荐

1、编辑

```sh
sudo vim /etc/sudoers
```

2、去掉前面#

```sh
%wheel ALL=(ALL)ALL
```

3、由于文件是只读，需加 ! 才能保存。

```sh
:wq!
```

### ssh 登陆

1、报错信息，禁止远程登陆

```sh
All configured authentication methods failed
Remote rejected opening a shell channel: Error: Not connected
```

2、编辑

```sh
sudo vim /etc/ssh/sshd_config
```

```sh
PermitRootLogin prohibit-password
```

改成

```sh
PermitRootLogin yes
```

3、重新启动 ssh

```sh
sudo systemctl restart sshd
```

4、开机启动 ssh

```sh
sudo systemctl enable --now sshd
```

5、查看 ssh 进程

```sh
ps -e | grep sshd
```

### 自定义内核

```sh
sudo pacman -S linux-lts linux-lts-headers
```

```sh
sudo pacman -S linux-zen linux-zen-headers
```

```sh
sudo pacman -S linux-hardened linux-hardened-headers
```

### Xorg（包含：xorg-server）

> https://wiki.archlinux.org/title/Xorg

```sh
sudo pacman -S xorg
```

- xorg-drivers（包含：显卡驱动）

```sh
sudo pacman -S xorg-drivers
```

- 可选

```sh
sudo pacman -S xorg-xinit
```

### Wayland（备选）

> https://wiki.archlinux.org/title/Wayland

#### AMD

```sh
sudo pacman -S mesa mesa-utils xf86-video-amdgpu
```

- 可选

```sh
sudo pacman -S vulkan-radeon lib32-vulkan-radeon
```

#### Intel

```sh
sudo pacman -S mesa mesa-utils xf86-video-intel
```

- 可选

```sh
sudo pacman -S vulkan-intel lib32-vulkan-intel
```

#### NVIDIA

> https://wiki.archlinux.org/title/NVIDIA

- 开源（谨慎）

```sh
sudo pacman -S mesa mesa-utils xf86-video-nouveau
```

- 闭源

```sh
sudo pacman -S nvidia nvidia-utils nvidia-settings
```

#### 虚拟机

```sh
sudo pacman -S mesa mesa-utils xf86-video-vesa xf86-video-vmware
```

### 音频

#### pipewire（推荐）

```sh
sudo pacman -S pipewire pipewire-alsa pipewire-pulse pipewire-jack pipewire-media-session
```

#### pulseaudio

```sh
sudo pacman -S alsa-utils pulseaudio pulseaudio-alsa
```

### 蓝牙

```sh
sudo pacman -S bluez bluez-utils
```

```sh
sudo pacman -S pulseaudio-bluetooth
```

1、查看蓝牙状态

```sh
systemctl status bluetooth
```

2、启动蓝牙

```sh
sudo systemctl start bluetooth
```

3、开机自启动蓝牙

```sh
sudo systemctl enable bluetooth
```

4、确保蓝牙未被阻止

```sh
rfkill list
```

5、取消阻止蓝牙

```sh
rfkill unblock bluetooth
```

### 鼠标

```sh
sudo pacman -S  xf86-input-vmmouse
```

### 触摸板

```sh
sudo pacman -S xf86-input-synaptics xf86-input-libinput
```

### 数位板

```sh
sudo pacman -S xf86-input-wacom libwacom
```

### 打印机

> https://wiki.archlinux.org/title/CUPS

```sh
sudo pacman -S cups libcups cups-filters cups-pk-helper system-config-printer
```

```sh
sudo systemctl enable cups
```

### 优化电源管理

```sh
sudo pacman -S powertop
```

```sh
sudo powertop --auto-tune
```

### 固态硬盘

1、启动

```sh
sudo systemctl start fstrim.service
```

2、开机启动

```sh
sudo systemctl enable fstrim.timer
```

### open-vm-tools

```sh
sudo pacman -S open-vm-tools
```

### 中文字体

```sh
sudo pacman -S noto-fonts-cjk noto-fonts-extra
```

### 桌面环境（先装xorg）

> https://wiki.archlinux.org/title/Desktop_environment

> https://wiki.archlinux.org/title/Display_manager

- 报错信息

```sh
warning: failed to retrieve some files
error: failed to commit transaction (failed to retrieve some files)
Errors occurred, no packages were upgraded.
```

- 数据同步

```sh
sudo pacman -Syy
```

#### GNOME

> https://wiki.archlinux.org/title/GNOME

```sh
sudo pacman -S gnome
```

##### gdm

```sh
sudo pacman -S gdm
```

```sh
sudo systemctl start gdm
```

```sh
sudo systemctl enable gdm
```

##### GNOME 设置分辨率

> 显示（Displays）→分辨率（Resolution）

#### KDE

> https://wiki.archlinux.org/title/KDE

##### plasma

```sh
sudo pacman -S plasma
```

##### plasma 最小化安装

```sh
sudo pacman -S plasma-desktop kscreen konsole
```

文件管理器（选装）

```sh
sudo pacman -S dolphin
```

##### sddm

```sh
sudo pacman -S sddm
```

```sh
sudo systemctl start sddm
```

```sh
sudo systemctl enable sddm
```

##### KDE 设置分辨率

> 系统设置（System Settings）→硬件（Hardware）→显示和监视（Display and Monitor）→显示配置（Display Configuration）→分辨率（Resolution）

##### KDE 设置中文界面

> 系统设置（System Settings）→个性化（Personalization）→语言和区域设置（Regional Settings）→语言（Language）→添加语言（Add Languages）-添加：简体中文，并拖到第一行

##### 解除锁屏

> 系统设置（System Settings）→工作区（Workspace）→工作区行为（Workspace Behavior）→锁屏（Screen Loking）→自动锁定屏幕（Lock screen automatically）取消：两个勾

- 系统重启，才能生效。

#### XFCE（轻量级）

```sh
sudo pacman -S xfce4
```

##### lightdm

```sh
sudo pacman -S lightdm lightdm-gtk-greeter lightdm-gtk-greeter-settings

```

```sh
sudo systemctl start lightdm
```

```sh
sudo systemctl enable lightdm
```

##### XFCE 报错信息

```sh
Job for lightdm.service failed because the control process exited with error code.
See "systemctl status lightdm.service" and "journalctl -xeu lightdm.service" for details.
```

##### XFCE 设置分辨率

> 显示（Display）→分辨率（Resolution）

## 中文输入法

### ibus

1、安装

```sh
sudo pacman -S ibus ibus-libpinyin
```

2、编辑

```sh
sudo vim $HOME/.xprofile
```

- 添加

```sh
export GTK_IM_MODULE=ibus
export XMODIFIERS=@im=ibus
export QT_IM_MODULE=ibus
ibus-daemon -x -d
```

3、刷新（重启生效）

```sh
source $HOME/.xprofile
```

4、ibus-setup

默认 "General"（常规）-选择 "Preferences"（首选项）-点击 "Input Methods"（输入法）-点击 "Add"（添加）————Chinese-Intelligent Pinyin

5、参考

> https://github.com/ibus/ibus/wiki

> https://wiki.archlinux.org/title/IBus

### fcitx5

1、安装 fcitx5

```sh
sudo pacman -S fcitx5  fcitx5-qt fcitx5-gtk fcitx5-configtool fcitx5-chinese-addons fcitx5-pinyin-zhwiki fcitx5-material-color
```

```sh
yay -S fcitx5-pinyin-moegirl
```

2、编辑

```sh
sudo vim /etc/environment
```

- 添加

```sh
GTK_IM_MODULE=fcitx
QT_IM_MODULE=fcitx
XMODIFIERS=@im=fcitx
SDL_IM_MODULE=fcitx
GLFW_IM_MODULE=ibus
```

3、重启系统生效

4、参考

> https://wiki.archlinux.org/title/Fcitx5

## 报错

### 无法启动 gnome-terminal、vim

```sh
vim /etc/locale.gen
```

- 去掉前面#

```sh
en_US.UTF-8 UTF-8
zh_CN.UTF-8 UTF-8
```

```sh
sudo locale-gen
```

```sh
sudo localectl set-locale LANG=en_US.UTF-8
sudo localectl set-locale LANG=zh_CN.UTF-8
```

### 系统中文改回英文

```sh
sudo vim /etc/default/locale
```

```sh
LANG="zh_CN.UTF-8"
LANGUAGE="zh_CN:zh"
```

改成

```sh
LANG="en_US.UTF-8"
LANGUAGE="en_US:en"
```

### 系统设置中文

> https://wiki.archlinux.org/title/Localization/Simplified_Chinese

1、编辑

```sh
sudo vim /etc/locale.gen
```

- 去掉前面#

```sh
en_US.UTF-8 UTF-8
zh_CN.UTF-8 UTF-8
```

2、执行 locale-gen 命令

```sh
locale-gen
```

3、警告：不推荐 LANG=zh_CN.UTF-8 写入 /etc/locale.conf，这会导致 tty 乱码。

4、建议在 vim ~/.bashrc 或者 vim ~/.xprofile 添加下面两行到文件*最开头*

```sh
export LANG=zh_CN.UTF-8
export LANGUAGE=zh_CN:en_US
```

5、系统重启，才能生效。
