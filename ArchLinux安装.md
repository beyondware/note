### 验证是否为 UEFI

```sh
ls /sys/firmware/efi/efivars
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
quit 或者 exit
```

### 更新系统时间

- 启动 ntp

```sh
timedatectl set-ntp true
```

- 查看时间状态

```sh
timedatectl status
```

### 修改镜像源

- 自动获取

1、获取 pacman 镜像源

```sh
reflector -c China -a 5 --sort rate --save /etc/pacman.d/mirrorlist
```

- 中国镜像源

```sh
sudo pacman-mirrors --country China
```

2、查看 pacman 镜像源

```sh
cat /etc/pacman.d/mirrorlist
```

- 手动添加

1、编辑配置文件

```sh
vim /etc/pacman.d/mirrorlist
```

2、添加镜像源（南京大学为例，放在最前面）

```sh
Server = https://mirror.nju.edu.cn/archlinux/$repo/os/$arch
Server = https://mirrors.tuna.tsinghua.edu.cn/archlinux/$repo/os/$arch
```

- Manjaro

```sh
sudo pacman-mirrors -i -c China -m rank
```

- 手动添加

```sh
Server = https://mirrors.tuna.tsinghua.edu.cn/manjaro/stable/$repo/$arch
```

3、更新 GPG key

```sh
sudo pacman -S archlinux-keyring
```

4、查看镜像源

```sh
cat /etc/pacman.d/mirrorlist
```

5、更新软件包缓存

```sh
sudo pacman -Syy
```

### 远程登陆

1、更新软件包缓存

```sh
pacman -Syy
```

2、安装 ssh 软件

```sh
pacman -S openssh
```

3、启动 ssh

```sh
systemctl start sshd
```

4、开机启动 ssh

```sh
systemctl enable sshd
```

5、查看 ssh 状态

```sh
systemctl status sshd
```

- active (running) 表示开启

6、设置 root 密码

```sh
passwd root
```

7、查看 IP 地址

```sh
ip add
```

### 分区

- fdisk 分区法

1、检查磁盘信息

```sh
fdisk -l
```

2、分区（sda：硬盘名）

```sh
fdisk /dev/sda
```

```sh
g：gpt 格式

n：创新分区

d：删除分区

p：查看分区
```

- 分区帮助信息

```sh
Help:

  DOS (MBR)
   a   toggle a bootable flag
   b   edit nested BSD disklabel
   c   toggle the dos compatibility flag

  Generic
   d   delete a partition（删除分区）
   F   list free unpartitioned space
   l   list known partition types
   n   add a new partition（添加新分区）
   p   print the partition table（打印分区表）
   t   change a partition type
   v   verify the partition table
   i   print information about a partition

  Misc
   m   print this menu（打印此菜单）
   u   change display/entry units
   x   extra functionality (experts only)

  Script
   I   load disk layout from sfdisk script file
   O   dump disk layout to sfdisk script file

  Save & Exit
   w   write table to disk and exit（将表写入磁盘并退出）
   q   quit without saving changes（退出而不保存更改）

  Create a new label
   g   create a new empty GPT partition table（创建一个新的空 GPT 分区表）
   G   create a new empty SGI (IRIX) partition table
   o   create a new empty DOS partition table
   s   create a new empty Sun partition table
```

```sh
Partition type
   p   primary (0 primary, 0 extended, 4 free)（主分区，最多4个）
   e   extended (container for logical partitions)（扩展分区）
```

- cfdisk 分区法

```sh
cfdisk /dev/sda
```

> 选择：gpt

```sh
/dev/sda1 512M EFI System

/dev/sda2 4G Linux swap

/dev/sda3 剩余 Linux filesystem
```

光标回到 Write，输入 yes，Quit 退出。

> Syncing disks.

- 如果没有显示，需要更新分区表（或者重启系统）

```sh
partprobe
```

### 格式化

- 一般分区 4 个

1、引导分区（512M）

> /boot/efi

2、交换分区

> swap

3、根分区

> /

- 格式化

1、boot 分区必须是 fat32 格式

```sh
mkfs.fat -F32 /dev/sda1
```

或者

```sh
mkfs.vfat /dev/sda1
```

2、交换分区（无需挂载）

- 创建 swap

```sh
mkswap /dev/sda2
```

- 激活 swap

```sh
swapon /dev/sda2
```

3、根目录，一般是 ext4 格式

```sh
mkfs.ext4 /dev/sda3
```

### 挂载

1、**必须**先挂载根目录

```sh
mount /dev/sda3 /mnt
```

2、引导分区挂载

```sh
mkdir -p /mnt/boot
```

```sh
mount /dev/sda1 /mnt/boot
```

3、查看挂载状态

```sh
lsblk -l
```

4、查看磁盘

```sh
df -h
```

### 安装软件

- 必装

```sh
pacstrap /mnt base base-devel linux linux-firmware
```

- 选装

```sh
pacstrap /mnt bash-completion git wget vim
```

### 生成 fstab 文件

```sh
genfstab -U /mnt >> /mnt/etc/fstab
```

- 查看是否有挂载信息

```sh
cat /mnt/etc/fstab
```

### 切换到物理安装的根分区

```sh
arch-chroot /mnt
```

### 更改时区

- 设置时区（一般为上海）

```sh
ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
```

- 设置硬件时间

```sh
hwclock --systohc
```

### 设置文本编码

```sh
vim /etc/locale.gen
```

删除`en_US.UTF-8`前面的`#`

- 输入 locale-gen

```sh
echo LANG=en_US.UTF-8 >> /etc/locale.conf
```

### 设置主机名

```sh
echo arch > /etc/hostname
```

- 以下内容粘贴到 vim /etc/hosts

```sh
127.0.0.1 localhost
::1 localhost
127.0.1.1 arch
```

### 添加 archlinuxcn 源

1、编辑配置文件

```sh
sudo vim /etc/pacman.conf
```

```sh
[archlinuxcn]
Server = https://mirrors.tuna.tsinghua.edu.cn/archlinuxcn/$arch
```

2、更新 GPG key

```sh
pacman -S archlinuxcn-keyring
```

3、更新软件包缓存

```sh
pacman -Syy
```

### 安装微指令

- 英特尔

```sh
pacman -S intel-ucode
```

- AMD

```sh
pacman -S amd-code
```

### 引导部署

1、安装 GRUB 引导加载程序和 EFI 引导管理器包

```sh
pacman -S efibootmgr os-prober grub grub-efi-x86_64
```

2、部署 GRUB

```sh
grub-install --target=x86_64-efi -bootloader-id=grub
```

```sh
grub-install –target=x86_64-efi –bootloader-id=grub_uefi
```

3、生成 GRUB 配置文件

```sh
grub-mkconfig -o /boot/grub/grub.cfg
```

4、查看生成配置文件

```sh
cat /boot/grub/grub.cfg
```

5、系统重启

- 退出 chroot 环境

```sh
exit
```

- 卸载挂载文件

```sh
umount /mnt/boot
umount /mnt
```

- 系统重启

```sh
reboot
```

### 物理机安装

1、安装显示服务器

```sh
sudo pacman -S  xorg xorg-server xorg-apps
```

2、安装 GNOME 桌面环境

```sh
sudo pacman -S gnome gnome-extra networkmanager
```

- KDE 桌面环境（另一种）

```sh
sudo pacman -S plasma kde-applications
```

3、登录桌面管理器

```sh
sudo pacman -S gdm
```

- 开机启动 gdm

```sh
sudo systemctl enable gdm
```

4、网络配置

```sh
sudo pacman -S dhcpcd
sudo pacman -S network-manager-applet
```

- 开机启动网络

```sh
sudo systemctl enable dhcpcd
sudo systemctl enable NetworkManager
```

5、中文输入法

```sh
sudo pacman -S fcitx5  fcitx5-qt fcitx5-gtk fcitx5-configtool fcitx5-chinese-addons fcitx5-pinyin-zhwiki
```

- 系统：sudo vim /etc/environment

```sh
GTK_IM_MODULE=fcitx
QT_IM_MODULE=fcitx
XMODIFIERS=@im=fcitx
INPUT_METHOD=fcitx
SDL_IM_MODULE=fcitx
GLFW_IM_MODULE=ibus
```

- 个人：sudo vi ~/.bash_profile

```sh
export XMODIFIERS=@im=fcitx
export GTK_IM_MODULE=fcitx
export QT_IM_MODULE=fcitx
```

- 系统重启
