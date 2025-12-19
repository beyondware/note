# Rocky Linux

## 换源

1、替换

```sh
sudo sed -e 's|^mirrorlist=|#mirrorlist=|g' \
         -e 's|^#baseurl=http://dl.rockylinux.org/$contentdir|baseurl=https://mirrors.cernet.edu.cn/rocky|g' \
         -i.backup \
         /etc/yum.repos.d/rocky-extras.repo \
         /etc/yum.repos.d/rocky.repo
```

2、生成缓存

```sh
sudo dnf makecache
```

3、参考

> https://help.mirrors.cernet.edu.cn/rocky/

## 安装桌面环境

1、组列出

```sh
dnf group list
```

2、组安装

```sh
dnf groupinstall "Server with GUI"
```

组移除

```sh
dnf groupremove "Server with GUI"
```

3、开启图形化

```sh
systemctl set-default graphical
```

## EPEL

### 安装 EPEL

```sh
sudo dnf install epel-release
```

```sh
sudo dnf repolist | grep epel
```

### 刷新更新

```sh
sudo dnf upgrade --refresh
```

### EPEL 软件源提供的软件包完整列表

```sh
dnf repository-packages epel list
```

### EPEL 软件源已安装的软件包

```sh
dnf repository-packages epel list installed
```

### 启用 EPEL 软件源

```sh
sudo dnf config-manager --set-enabled epel
```

禁用 EPEL 软件源

```sh
sudo dnf config-manager --set-disabled epel
```

# Fedora

## 换源

### 方案一（推荐）

1、替换

```sh
sudo sed -e 's|^metalink=|#metalink=|g' \
         -e 's|^#baseurl=http://download.example/pub/fedora/linux|baseurl=https://mirrors.cernet.edu.cn/fedora|g' \
         -i.backup \
         /etc/yum.repos.d/fedora.repo \
         /etc/yum.repos.d/fedora-modular.repo \
         /etc/yum.repos.d/fedora-updates.repo \
         /etc/yum.repos.d/fedora-updates-modular.repo
```

2、生成缓存

```sh
sudo dnf makecache
```

### 方案二

1、切换目录

```sh
cd /etc/yum.repos.d/
```

```sh
sudo wget -O /etc/yum.repos.d/fedora.repo http://mirrors.aliyun.com/repo/fedora.repo
```

```sh
sudo wget -O /etc/yum.repos.d/fedora-updates.repo http://mirrors.aliyun.com/repo/fedora-updates.repo
```

2、生成缓存

```sh
sudo dnf makecache
```

### 参考

> https://developer.aliyun.com/mirror/fedora

> https://help.mirrors.cernet.edu.cn/fedora/

## 提高 dnf 速度

1、dnf 配置文件

```sh
sudo vim /etc/dnf/dnf.conf
```

2、文件底部追加

```sh
[main]
fastestmirror=true             ## 选择最快镜像源
deltarpm=true                  ## 增量下载
max_parellel_downloads=10      ## 最大并行下载数量
```

3、刷新

```sh
sudo dnf upgrade --refresh
或者
sudo dnf makecache
```

## dnf-automatic

1、安装 dnf-automatic

```sh
sudo dnf install dnf-automatic
```

2、编辑

```sh
sudo vim /etc/dnf/automatic.conf
```

3、修改为

```sh
[commands]
apply_updates = yes

[emitters]
emit_via = motd

[base]
debuglevel = 1
```

4、升级

```sh
sudo dnf upgrade
```

5、开机自启动

```sh
sudo systemctl enable --now dnf-automatic.timer
```

## 系统版本升级

1、刷新

```sh
sudo dnf upgrade --refresh
```

- 注：不要跳过此步骤，重启系统。

2、安装 dnf-plugin-system-upgrade

```sh
sudo dnf install dnf-plugin-system-upgrade
```

3、下载最新 Fedora 更新包

```sh
sudo dnf system-upgrade download --releasever=42  说明：42 为版本号
```

4、升级并重启

```sh
sudo dnf system-upgrade reboot
```

5、验证更新版本

```sh
cat /etc/fedora-release
```

6、参考

> https://docs.fedoraproject.org/en-US/quick-docs/dnf-system-upgrade/

# 家目录

## 中文改为英文

### 方案一（推荐）

```sh
export LANG=en_US
```

```sh
xdg-user-dirs-gtk-update
```

> 勾选：不要再次询问我（Don't ask me this again）

> 点击：更新名称（Update Names）

### 方案二

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

2、修改

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

## 英文改为中文

```sh
export LANG=zh_CN.UTF-8
```

```sh
xdg-user-dirs-gtk-update
```

# 快捷键打开 gnome-terminal

设置-键盘-自定义快捷键

```sh
名称：open in terminal
命令：/usr/bin/gnome-terminal
快捷键：Ctrl+Alt+T
```

# 启用「最小化」和「最大化」按钮

1、右边按钮

```sh
gsettings set org.gnome.desktop.wm.preferences button-layout ":minimize,maximize,close"
```

2、左边按钮

```sh
gsettings set org.gnome.desktop.wm.preferences button-layout "close,minimize,maximize:"
```

# 「回收站」图标

1、启用

```sh
gsettings set org.gnome.shell.extensions.ding show-trash true
```

2、禁用

```sh
gsettings set org.gnome.shell.extensions.ding show-trash false
```

# 「主目录」文件夹图标

1、显示

```sh
gsettings set org.gnome.shell.extensions.ding show-home true
```

2、隐藏

```sh
gsettings set org.gnome.shell.extensions.ding show-home false
```

# 选装

## open-vm-tools

```sh
sudo dnf install open-vm-tools open-vm-tools-desktop
```

## gnome-tweaks

```sh
sudo dnf install gnome-tweaks
```

## gnome-extensions

```sh
sudo dnf install gnome-extensions-app
```

## dash-to-dock（重启生效）

```sh
sudo dnf install gnome-shell-extension-dash-to-dock
```

> https://extensions.gnome.org/extension/307/dash-to-dock/

# 特效

扩展安装位置

```sh
cd ~/.local/share/gnome-shell/extensions
```

## Compiz windows effect（晃动效果）

> https://extensions.gnome.org/extension/3210/compiz-windows-effect/

## Compiz alike magic lamp effect（魔术灯效果）

> https://extensions.gnome.org/extension/3740/compiz-alike-magic-lamp-effect/

## Coverflow Alt-Tab（组合键【Alt】+【Tab】切换效果）

> https://extensions.gnome.org/extension/97/coverflow-alt-tab/

# 美化

## 主题

```sh
git clone https://github.com/vinceliuice/WhiteSur-gtk-theme.git
```

```sh
cd WhiteSur-gtk-theme/
```

```sh
./install.sh
```

主题默认位置

```sh
cd ~/.themes
```

## 图标

```sh
git clone https://github.com/vinceliuice/WhiteSur-icon-theme.git
```

```sh
cd WhiteSur-icon-theme/
```

```sh
./install.sh
```

图标默认位置

```sh
cd ~/.local/share/icons
```

## 光标

```sh
git clone https://github.com/vinceliuice/WhiteSur-cursors.git
```

```sh
cd WhiteSur-cursors/
```

```sh
./install.sh
```

光标默认位置

```sh
 cd ~/.local/share/icons
```

## 壁纸

```sh
git clone https://github.com/vinceliuice/WhiteSur-wallpapers.git
```

```sh
cd WhiteSur-wallpapers/
```

```sh
sudo ./install-gnome-backgrounds.sh
```

壁纸默认位置

```sh
cd /usr/share/backgrounds
```

# 编译报错汇总

1、configure: error: Cannot build a 32-bit program, you need to install 32-bit development libraries.

```sh
./configure --enable-win64
```

2、configure: error: no acceptable C compiler found in $PATH

```sh
sudo dnf install gcc-c++
```

3、configure: error: no suitable flex found. Please install the 'flex' package.

```sh
sudo dnf install flex
```

4、configure: error: no suitable bison found. Please install the 'bison' package.

```sh
sudo dnf install bison
```

5、configure: error: X 64-bit development files not found. Wine will be built

```sh
sudo dnf install libX11-devel
```

6、configure: error: FreeType 64-bit development files not found. Fonts will not be built.

```sh
sudo dnf install freetype-devel
```

7、fatal error: X11/extensions/Xrandr.h: No such file or directory

```sh
sudo dnf install libXrandr-devel
```
