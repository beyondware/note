### SSH 登录

1、安装 SSH

```sh
sudo apt install openssh-server
```

2、启动 SSH

```sh
sudo systemctl start sshd
```

3、允许 SSH 远程登陆（root 登录）

```sh
sudo vim /etc/ssh/sshd_config
```

> PermitRootLogin without-password 修改为 PermitRootLogin yes

4、重启 SSH

```sh
sudo systemctl restart sshd
```

5、开机启动 SSH

```sh
sudo systemctl enable sshd
```

6、查看 SSH 状态

```sh
sudo systemctl status sshd
```

7、查看 SSH 进程

```sh
ps -e | grep sshd
```

> 显示 00:00:00 sshd 表示开启了 SSH

### 修改镜像源

```sh
sudo vim /etc/apt/sources.list
```

官方源

> http://archive.ubuntu.com/ubuntu/

阿里云

> https://developer.aliyun.com/mirror/ubuntu

清华大学

> https://mirrors.tuna.tsinghua.edu.cn/help/ubuntu/

### 常用命令

#### 安装

```sh
sudo apt install 包名
```

#### 下载安装

```sh
sudo dpkg -i 本地包.deb
```

- 报错的话，需要修复依赖项

```sh
sudo apt install -f
```

#### 卸载

```sh
sudo apt remove 包名
```

```sh
dpkg uninstall 包名
```

- 自动卸载

```sh
sudo apt autoremove 包名
```

- 删除包和依赖

```sh
sudo apt purge 包名
```

#### 列出

列出与该包关联文件

```sh
sudo apt list --installed | grep -i 包的关键字
```

```sh
dpkg -L | grep 包的关键字
```

#### 更新

更新包缓存（只获得包的最新信息，并不会下载或者安装包）

```sh
sudo apt update
```

#### 升级

1、升级包到最新版本（下载和升级到最新版本）

```sh
sudo apt upgrade 包名
```

- 自动处理依赖项升级包

```sh
sudo apt full-upgrade 包名
```

2、查看可升级的软件包

```sh
apt list --upgradable
```

3、仅升级指定的软件包

```sh
sudo apt install --only-upgrade 包名
```

4、模拟升级（但不升级任何包）

```sh
apt -s upgrade
```

#### 搜索

```sh
apt search 包名
```

#### 详细信息

1、显示包的详细信息

```sh
apt show 包名
```

2、获取详细信息

```sh
apt info 包名
```

### 终端美化

终端-点击“三杠”-配置文件首选项

- 文本和背景颜色：Solarized
- 调色板：Solarized
