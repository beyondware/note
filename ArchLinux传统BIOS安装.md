### SSH 登陆

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

### 修改镜像源

1、编辑

```sh
vim /etc/pacman.d/mirrorlist
```

2、添加镜像源（南京大学为例）

```sh
Server = https://mirror.nju.edu.cn/archlinux/$repo/os/$arch
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

### cfdisk 分区法

1、确认磁盘名

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
/dev/sda1 1G Linux swap
/dev/sda2 剩余 Linux filesystem
```

5、光标回到 Write，输入 yes，Quit 退出。

> Syncing disks.

### 挂载分区

1、查看磁盘信息

```sh
fdisk -l
```

2、swap分区

```sh
mkswap /dev/sda1
swapon /dev/sda1
```

3、挂载根目录

```sh
mkfs.ext4 /dev/sda2
```

```sh
mount /dev/sda2 /mnt
```

### 必备软件

```sh
pacstrap /mnt base linux linux-firmware dhcpcd vim openssh xfsprogs man net-tools
```

### 生成 fstab 文件

```sh
genfstab -U /mnt >> /mnt/etc/fstab
```

- 查看信息

```sh
cat /mnt/etc/fstab
```

### 更改根目录

```sh
arch-chroot /mnt
```

### 更改时区

```sh
ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
```

```sh
hwclock --systohc
```

### 设置文本编码

```sh
vim /etc/locale.gen
```

- 去掉前面的#

```sh
en_US.UTF-8 UTF-8
```

- 输入 locale-gen，生成 locale 信息

```sh
echo LANG=en_US.UTF-8 >> /etc/locale.conf
```

### 设置主机名

```sh
echo arch > /etc/hostname
```

- 编辑

```sh
vim /etc/hosts
```

```sh
127.0.0.1   localhost
::1      localhost
127.0.1.1   arch.localdomain arch
```

### 安装 CPU 微指令

```sh
pacman -S intel-ucode
```

### 网络

1、安装 NetworkManager（必须先装，不然新系统无法联网）

```sh
pacman -S networkmanager
```

```sh
systemctl enable NetworkManager
```

2、启动 dhcpcd

```sh
systemctl enable dhcpcd
```

3、启动

```sh
systemctl enable sshd
```

4、修改SSH登录

```sh
sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/g' /etc/ssh/sshd_config
```

```sh
systemctl restart sshd
```

### GRUB 引导

> https://wiki.archlinux.org/title/GRUB

```sh
pacman -S grub
```

1、查看磁盘信息

```sh
fdisk -l
```

2、执行 grub-install 报错

```sh
Installing for i386-pc platform.
grub-install: warning: this GPT partition label contains no BIOS Boot Partition; embedding won't be possible.
grub-install: warning: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
grub-install: error: will not proceed with blocklists.
```

2、安装 parted

```sh
pacman -S parted
```

3、
```sh
parted /dev/sda set 1 bios_grub on
```

> nformation: You may need to update /etc/fstab.

```sh
parted /dev/sda print
```

4、（整块硬盘sda）

```sh
grub-install /dev/sda
```

5、输出以下信息，表示成功。

```sh
Installing for i386-pc platform.
Installation finished. No error reported.
```

### 导出grub配置文件

```sh
grub-mkconfig -o /boot/grub/grub.cfg
```

### 设置 root 密码（新系统登陆）

```sh
passwd root
```

### 退出 chroot 环境

```sh
exit
```

### 卸载挂载点

```sh
umount  -R /mnt
```

- 查看挂载状态

```sh
lsblk -l
```

### 系统重启

```sh
reboot
```
------

### 登陆 ssh（新系统）

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

### 无法登陆 SSH

1、报错信息

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
LoginGraceTime 120
PermitRootLogin yes
StrictModes yes
```

3、重新启动 SSH

```sh
systemctl restart sshd
```

### 添加新的用户

1、添加用户到 wheel 组

```sh
useradd -m -g users -G wheel -s /bin/bash 用户名
```

2、设置用户密码

```sh
passwd 用户名
```

3、设置 wheel 组权限

```sh
pacman -S sudo
```

- 编辑 sudo vim /etc/sudoers 或者 EDITOR=vim visudo （推荐）去掉前面的#

```sh
%wheel ALL=(ALL)ALL
```

### 桌面环境

- GNOME

```sh
sudo pacman -S gnome
```

### 登录界面

- gdm（GNOME）

```sh
sudo pacman -S gdm
```

```sh
sudo systemctl enable gdm
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

```sh
GTK_IM_MODULE=fcitx
QT_IM_MODULE=fcitx
XMODIFIERS=@im=fcitx
SDL_IM_MODULE=fcitx
GLFW_IM_MODULE=ibus
```

3、系统重启生效

### archlinuxcn 源

1、编辑配置文件

```sh
sudo vim /etc/pacman.conf
```

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

- AMD

```sh
sudo pacman -S mesa lib32-mesa xf86-video-amdgpu
```

- 可选

```sh
sudo pacman -S vulkan-radeon lib32-vulkan-radeon
```

- Intel

```sh
sudo pacman -S mesa lib32-mesa xf86-video-intel
```

- 可选

```sh
sudo pacman -S vulkan-intel lib32-vulkan-intel
```

- NVIDIA

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
