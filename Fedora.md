### SSH

- 远程拒绝打开外壳通道:错误:未连接，需要启动 SSH

> Remote rejected opening a shell channel: Error: Not connected

1、查看 SSH 状态

```sh
systemctl status sshd
```

> Active: active (running) 表示开启

> Active: inactive (dead) 表示关闭

2、启动 SSH

```sh
sudo systemctl start sshd
```

3、开机启动 SSH

```sh
sudo systemctl enable sshd
```

4、停止 SSH

```sh
sudo systemctl stop sshd
```

5、重启 SSH

```sh
sudo systemctl restart sshd
```

6、查看 SSH 连接状态

```sh
ps -e | grep ssh
```

> 显示 00:00:00 sshd 表示连接上了 SSH

### 快捷键打开终端

- 设置-键盘快捷键

```sh
名称：open in terminal
命令：/usr/bin/gnome-terminal
快捷键：Ctrl+Alt+T
```

### 镜像源

1、切换路径

> cd /etc/yum.repos.d/

```sh
sudo wget -O /etc/yum.repos.d/fedora.repo http://mirrors.aliyun.com/repo/fedora.repo
sudo wget -O /etc/yum.repos.d/fedora-updates.repo http://mirrors.aliyun.com/repo/fedora-updates.repo
```

2、本地缓存

```sh
sudo dnf makecache
```

3、参考源

- 阿里云

> https://developer.aliyun.com/mirror/fedora

- 腾讯云

> https://mirrors.cloud.tencent.com/help/fedora.html

- 清华大学

> https://mirrors.tuna.tsinghua.edu.cn/help/fedora/

- 中国科学技术大学

> https://mirrors.ustc.edu.cn/help/fedora.html

### RPM Fusion

> https://rpmfusion.org/Configuration

1、检查是否已安装 RPM fusion

```sh
dnf repolist | grep rpmfusion
```

2、安装 RPM fusion

#### Fedora

```sh
sudo dnf install https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm
sudo dnf install https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
```

#### Silverblue、Kinoite、CoreOS

```sh
sudo rpm-ostree install https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm
sudo rpm-ostree install https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
```

3、查看添加的仓库列表

```sh
dnf repolist
```

4、删除 RPM fusion

```sh
rpm -qa 'rpmfusion*'  //列出
```

```sh
sudo dnf remove rpmfusion-free-release rpmfusion-nonfree-release
```

### 家目录

#### 家目录英文改为中文

方案一（推荐）

```sh
export LANG=en_US
```

```sh
xdg-user-dirs-gtk-update
```

> 勾选：不要再次询问我（Don't ask me this again）

> 点击：更新名称（Update Names）

方案二（备选）

① 先将中文目录对应重命名为英文

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

② 修改配置

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

③ 系统重启，才能生效。

#### 家目录英文改为中文

```sh
export LANG=zh_CN.UTF-8
```

```sh
xdg-user-dirs-gtk-update
```

### gnome-tweaks

```sh
sudo dnf install gnome-tweaks
```

### 显示 Dock 栏

> https://extensions.gnome.org/

- 由于 GNOME 42 目前暂不支持，用命令安装，重启系统才能生效。

> https://extensions.gnome.org/extension/307/dash-to-dock/

```sh
sudo dnf install gnome-shell-extension-dash-to-dock.noarch
```

### 特效扩展

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

### 主题

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

### 图标

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

### 光标

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

### 壁纸

> https://github.com/vinceliuice/WhiteSur-wallpapers

```sh
git clone https://ghproxy.com/https://github.com/vinceliuice/WhiteSur-wallpapers.git
```

```sh
cd WhiteSur-wallpapers/
```

- 注意：需要权限

```sh
sudo ./install-gnome-backgrounds.sh
```

- 壁纸默认位置

```sh
cd /usr/share/backgrounds
```