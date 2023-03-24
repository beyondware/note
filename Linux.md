## SSH

- 远程拒绝打开外壳通道:错误:未连接，需要启动 SSH

> Remote rejected opening a shell channel: Error: Not connected

### 安装 SSH

- Debian、Ubuntu

```sh
sudo apt install openssh-server
```

### 查看 SSH 状态

```sh
systemctl status sshd
```

> Active: active (running) 表示开启

> Active: inactive (dead) 表示关闭

### 启动 SSH

```sh
sudo /etc/init.d/ssh start
```

或者

```sh
sudo systemctl start sshd
```

### 开机启动 SSH

```sh
sudo systemctl enable sshd
```

### 停止 SSH

```sh
sudo systemctl stop sshd
```

### 重启 SSH

```sh
sudo systemctl restart sshd
```

### 允许 SSH 远程登陆

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

### 查看 SSH 连接状态

```sh
ps -e | grep ssh
```

> 显示 00:00:00 sshd 表示连接上了 SSH

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

## Linux内核版本

```sh
uname -a
```

```sh
hostnamectl | grep -i kernel
```

```sh
cat /proc/version
```

## 查看无线网卡型号

```sh
lspci
lspci | grep Network
lspci | grep -i net
```

```sh
nmcli radio
nmcli radio wifi on
```
