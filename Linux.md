## SSH

> sshd（Fedora）或者 ssh（Debian），具体情况而定。

### 安装 SSH

> Unit sshd.service could not be found.

#### Debian

```sh
sudo apt install openssh-server
```

#### Fedora

- 查看是否安装

```sh
rpm -qa | grep openssh-server
```

- 安装

```sh
sudo dnf install openssh-server

```

- 查看版本

```sh
ssh -V
```

### 查看 SSH

```sh
systemctl status sshd 或者 sudo /etc/init.d/ssh status 或者 service sshd status
```

> Active: active (running) 表示开启

> Active: inactive (dead) 表示关闭

### 启动 SSH

```sh
sudo systemctl start sshd 或者 sudo /etc/init.d/ssh start 或者 service sshd start
```

### 开机启动 SSH

```sh
sudo systemctl enable sshd 或者 sudo systemctl enable ssh
```

### 禁止开机启动 SSH

```sh
sudo systemctl disable sshd
```

### 停止 SSH

```sh
sudo systemctl stop sshd 或者 sudo /etc/init.d/ssh stop 或者 service sshd stop
```

### 重启 SSH

```sh
sudo systemctl restart sshd 或者 sudo /etc/init.d/ssh restart 或者 service sshd restart
```

### 允许 SSH 远程登陆

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

### 查看运行状态

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

## Linux 内核版本

```sh
uname -a
```

```sh
hostnamectl | grep -i kernel
```

- 显示的信息更详细

```sh
cat /proc/version
```

## 查看无线网卡型号

```sh
lspci
```

```sh
lspci | grep Network
```

```sh
lspci | grep -i net
```

## 查看 WiFi 是否打开

```sh
nmcli radio
```

```sh
nmcli radio wifi on
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
