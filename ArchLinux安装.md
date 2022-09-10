## 准备工作

### Arch 安装指南

> https://wiki.archlinux.org/title/Installation_guide

### VMware Workstation 设置

> 编辑虚拟机设置→选项-高级-固件类型，改成：UEFI

### 是否为 UEFI

```sh
ls /sys/firmware/efi/efivars
```

### 设置终端字体大小

```sh
setfont ter-132n
```

### 联网

- 有线网络

```sh
dhcpcd
```

- 无线网络

1、进入 iwd 环境

```sh
iwctl
```

2、列出网卡设备

```sh
device list
```

3、扫描网络（wlan0：无线网卡号）

```sh
station wlan0 scan
```

4、列出扫描到的网络

```sh
station wlan0 get-networks
```

5、连接无线网络

```sh
station wlan0 connect 网络名称
```

6、退出 iwd 环境

```sh
exit
```

### ssh 登陆

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

4、设置 root 密码

```sh
passwd root
```

5、查看 IP 地址

```sh
ip addr
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
/dev/sda2 1G Linux swap
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
mkfs.fat -F32 /dev/sda1
```

或者

```sh
mkfs.vfat /dev/sda1
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

- 支持大文件

```sh
mkfs.xfs /dev/sda3
```

- **必须**先挂载根目录

```sh
mount /dev/sda3 /mnt
```

5、引导 EFI 分区

```sh
mkdir -p /mnt/efi
```

```sh
mount /dev/sda1 /mnt/efi
```

### 更新系统时间

```sh
timedatectl set-ntp true
```

```sh
timedatectl status
```

### 修改镜像源

#### 自动获取

```sh
reflector --country China --age 72 --sort rate --protocol https --save /etc/pacman.d/mirrorlist
```

#### 手动添加

1、编辑

```sh
vim /etc/pacman.d/mirrorlist
```

2、添加镜像源

```sh
Server = https://mirror.nju.edu.cn/archlinux/$repo/os/$arch
Server = https://mirrors.tuna.tsinghua.edu.cn/archlinux/$repo/os/$arch
```

3、更新软件包缓存

```sh
pacman -Syy
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

2、grub-install

```sh
grub-install /dev/sda
```

- 输出以下信息，表示成功。

```sh
Installing for i386-pc platform.
Installation finished. No error reported.
```

3、导出 grub 配置文件

```sh
grub-mkconfig -o /boot/grub/grub.cfg
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

4、安装（整块硬盘：sda）

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

2、挂载

```sh
mount /dev/sda1 /mnt/efi
```

3、安装引导检测器

```sh
pacman -S os-prober
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

6、生成 GRUB 配置文件

```sh
grub-mkconfig -o /boot/grub/grub.cfg
```

7、查看生成配置文件

```sh
cat /boot/grub/grub.cfg
```

- 查看是否包含`initramfs-linux-fallback.img initramfs-linux.img intel-ucode.img vmlinuz-linux`文件

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

- 去掉前面#

```sh
en_US.UTF-8 UTF-8
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

- Intel

```sh
pacman -S intel-ucode
```

- AMD

```sh
pacman -S amd-ucode
```

### NetworkManager

- 必须先装，不然新系统无法联网

```sh
pacman -S networkmanager
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

### 设置 root 密码

- 登陆新系统使用

```sh
passwd root
```

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

## 新系统

### ssh 登陆

1、安装 openssh

```sh
pacman -S openssh
```

2、开启 ssh

```sh
systemctl start sshd
```

### ssh 登陆失败

1、报错，禁止远程登陆

```sh
All configured authentication methods failed
Remote rejected opening a shell channel: Error: Not connected
```

2、编辑 SSH 配置文件

```sh
vim /etc/ssh/sshd_config
```

- 修改为

```sh
PermitRootLogin yes
```

3、重新启动 SSH

```sh
systemctl restart sshd
```

4、开机启动 ssh

```sh
systemctl enable sshd
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

3、设置 wheel 组权限

```sh
pacman -S sudo
```

4、编辑

```sh
sudo vim /etc/sudoers 或者 EDITOR=vim visudo （推荐）
```

- 去掉前面#

```sh
%wheel ALL=(ALL)ALL
```

### 桌面环境

- GNOME

```sh
sudo pacman -S gnome
```

- KDE

```sh
sudo pacman -S plasma
```

### 开机登录界面

- gdm（GNOME）

```sh
sudo pacman -S gdm
```

```sh
sudo systemctl enable gdm
```

- sddm（KDE）

```sh
sudo pacman -S sddm
```

```sh
sudo systemctl enable sddm
```

### 中文字体

```sh
sudo pacman -S wqy-microhei wqy-zenhei noto-fonts-cjk noto-fonts-emoji
```

### fcitx5 输入法

> https://wiki.archlinux.org/title/Fcitx5

1、安装 fcitx5

```sh
sudo pacman -S fcitx5  fcitx5-qt fcitx5-gtk fcitx5-configtool fcitx5-chinese-addons fcitx5-pinyin-zhwiki fcitx5-material-color
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

3、重启生效

### 添加 archlinuxcn 源

1、编辑配置文件

```sh
sudo vim /etc/pacman.conf
```

- 添加

```sh
[archlinuxcn]
Server = https://mirrors.tuna.tsinghua.edu.cn/archlinuxcn/$arch
```

2、更新软件包缓存

```sh
sudo pacman -Syy
```

3、更新 GPG key

```sh
sudo pacman -S archlinuxcn-keyring
```

4、如果遇到一连串error

```sh
rm -rf /etc/pacman.d/gnupg
pacman-key --init
pacman-key --populate archlinux archlinuxcn
pacman -Syy
```

## 驱动

### Xorg

```sh
sudo pacman -S  xorg xorg-drivers
```

### 显卡

1、AMD

```sh
sudo pacman -S mesa lib32-mesa xf86-video-amdgpu
```

- 可选

```sh
sudo pacman -S vulkan-radeon lib32-vulkan-radeon
```

2、Intel

```sh
sudo pacman -S mesa lib32-mesa xf86-video-intel
```

- 可选

```sh
sudo pacman -S vulkan-intel lib32-vulkan-intel
```

3、NVIDIA

```sh
sudo pacman -S mesa lib32-mesa xf86-video-nouveau
```

- 可选

```sh
sudo pacman -S nvidia nvidia-settings lib32-nvidia-utils
```

### 视频驱动

```sh
sudo pacman -S xf86-video-vesa xf86-video-vmware
```

### 音频

```sh
sudo pacman -S pipewire pipewire-alsa pipewire-jack pipewire-media-session
```

### 蓝牙

```sh
sudo pacman -S pulseaudio-bluetooth
```

```sh
sudo systemctl enable bluetooth
```

### 鼠标

```sh
sudo pacman -S  xf86-input-vmmouse xf86-input-libinput xf86-input-synaptics
```

### 打印机

```sh
sudo pacman -S cups cups-filters libcups cups-pk-helper system-config-printer
```

```sh
sudo systemctl enable cups
```

### 固态硬盘优化

1、启动

```sh
sudo systemctl start fstrim.service
```

2、开机启动

```sh
sudo systemctl enable fstrim.timer
```

## 其他

### gnome-terminal 无法启动

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

### 系统显示中文改回英文

```sh
vim /etc/default/locale
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
