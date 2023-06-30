# Rocky Linux

## 镜像源

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

3、开启图形化

```sh
systemctl set-default graphical
```

4、组移除

```sh
dnf groupremove "Server with GUI"
```

# Fedora

## 镜像源

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

3、参考

> https://help.mirrors.cernet.edu.cn/fedora/

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

3、参考

> https://developer.aliyun.com/mirror/fedora

> https://mirrors.cloud.tencent.com/help/fedora.html

> https://mirrors.tuna.tsinghua.edu.cn/help/fedora/

> https://mirrors.ustc.edu.cn/help/fedora.html

## 系统版本升级

1、更新 Fedora 系统

```sh
sudo dnf upgrade --refresh
```

- 注：不要跳过此步骤，重新启动计算机。

2、安装 dnf-plugin-system-upgrade

```sh
sudo dnf install dnf-plugin-system-upgrade
```

3、下载最新 Fedora 更新包

```sh
sudo dnf system-upgrade download --releasever=38
```

4、开始升级

```sh
sudo dnf system-upgrade reboot
```

5、验证更新版本

```sh
cat /etc/fedora-release
```

6、参考

> https://docs.fedoraproject.org/en-US/quick-docs/dnf-system-upgrade/

# 优化界面

> https://github.com/lxde/lxappearance

- 更改主题、图标、鼠标的工具

1、优化

```sh
sudo dnf install gnome-tweaks
```

2、扩展

```sh
sudo dnf install gnome-extensions-app
```

3、Dock（重启生效）

```sh
sudo dnf install gnome-shell-extension-dash-to-dock
```

> https://extensions.gnome.org/extension/307/dash-to-dock/

# 特效扩展

- 扩展安装位置

```sh
cd ~/.local/share/gnome-shell/extensions
```

1、Compiz windows effect：晃动效果

> https://extensions.gnome.org/extension/3210/compiz-windows-effect/

2、Compiz alike magic lamp effect：魔术灯效果

> https://extensions.gnome.org/extension/3740/compiz-alike-magic-lamp-effect/

3、Coverflow Alt-Tab：组合键“Alt+Tab”切换效果

> https://extensions.gnome.org/extension/97/coverflow-alt-tab/

# 美化界面

## 主题

> https://github.com/vinceliuice/WhiteSur-gtk-theme

```sh
git clone https://ghproxy.com/https://github.com/vinceliuice/WhiteSur-gtk-theme.git
```

```sh
cd WhiteSur-gtk-theme/
```

```sh
./install.sh
```

- 主题默认位置

```sh
cd ~/.themes
```

## 图标

> https://github.com/vinceliuice/WhiteSur-icon-theme

```sh
git clone https://ghproxy.com/https://github.com/vinceliuice/WhiteSur-icon-theme.git
```

```sh
cd WhiteSur-icon-theme/
```

```sh
./install.sh
```

- 图标默认位置

```sh
cd ~/.local/share/icons
```

## 光标

> https://github.com/vinceliuice/WhiteSur-cursors

```sh
git clone https://ghproxy.com/https://github.com/vinceliuice/WhiteSur-cursors.git
```

```sh
cd WhiteSur-cursors/
```

```sh
./install.sh
```

- 光标默认位置

```sh
 cd ~/.local/share/icons
```

## 壁纸

> https://github.com/vinceliuice/WhiteSur-wallpapers

```sh
git clone https://ghproxy.com/https://github.com/vinceliuice/WhiteSur-wallpapers.git
```

```sh
cd WhiteSur-wallpapers/
```

```sh
sudo ./install-gnome-backgrounds.sh
```

- 壁纸默认位置

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

