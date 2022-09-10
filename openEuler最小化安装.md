### 分区

```sh
/boot/efi 500M 引导分区
swap 2GB 交换分区
/ 剩余 根目录
```

### 联网

- 正常不用管

```sh
vi /etc/sysconfig/network-scripts/ifcfg-ens33
```

- ONBOOT=no 改成 yes

### SSH 登陆

```sh
vi /etc/ssh/sshd_config
```

- PermitRootLogin no 改成 yes

### 修改源

```sh
vi /etc/yum.repos.d/openEuler.repo
```

> http://repo.openeuler.org/

改成（可选）

> https://repo.huaweicloud.com/openeuler/

> https://mirrors.nju.edu.cn/openeuler/

> https://mirrors.tuna.tsinghua.edu.cn/openeuler/

### GNOME 最小化安装

1、系统更新

```sh
sudo dnf update
```

2、中文字体（否则乱码）

- 文泉驿

```sh
sudo dnf install wqy-microhei-fonts wqy-zenhei-fonts
```

- 思源字体（选装）

```sh
sudo dnf install google-noto-sans-cjk-sc-fonts google-noto-serif-cjk-sc-fonts
```

#### gdm

1、安装 gdm

```sh
sudo dnf install gdm
```

2、开机启动 gdm

```sh
sudo systemctl enable gdm
```

#### lightdm

1、安装 lightdm

```sh
sudo dnf install lightdm lightdm-gtk
```

```sh
echo 'user-session=gnome' >> /etc/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf
```

2、启动 lightdm

```sh
sudo systemctl start lightdm
```

3、开机启动 lightdm

```sh
sudo systemctl enable lightdm
```

### 图形化登录

```sh
sudo systemctl set-default graphical.target
```

### 重启系统

```sh
sudo reboot
```

### 选装

1、文件管理器

```sh
sudo dnf install nautilus
```

2、终端

```sh
sudo dnf install gnome-terminal
```

- 设置-键盘快捷键

```sh
名称：open in terminal
命令：/usr/bin/gnome-terminal
快捷键：Ctrl+Alt+T
```
