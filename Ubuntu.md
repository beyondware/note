### SSH 登录

1、安装 SSH

```sh
sudo apt install openssh-server
```

或者

```sh
sudo apt install ssh
```

2、启动 SSH

```sh
sudo systemctl start ssh
```

3、允许 SSH 远程登陆（root 登录）

```sh
sudo vim /etc/ssh/sshd_config
```

> PermitRootLogin without-password 修改为 PermitRootLogin yes

4、重启 SSH

```sh
sudo systemctl restart ssh
```

5、开机启动 SSH

```sh
sudo systemctl enable ssh
```

6、查看 SSH 状态

```sh
sudo systemctl status sshd
```

7、查看 SSH 进程

```sh
ps -e | grep ssh
```

> 显示 00:00:00 sshd 表示开启了 SSH

### 常用命令

1、安装

```sh
apt install
```

2、卸载

```sh
apt remove
```

```sh
dpkg uninstall
```

- 自动卸载

```sh
apt autoremove
```

- 删除包和配置

```sh
apt purge
```

3、列出与该包关联文件

```sh
apt list --installed | grep -i 包的关键字
```

```sh
dpkg -L | grep 包
```

4、更新本地包仓库缓存（更新）

```sh
apt update
```

5、升级所有可升级包（升级）

```sh
apt upgrade
```

- 自动处理依赖项升级包

```sh
apt full-upgrade
```

6、查看可升级的软件包

```sh
apt list --upgradable
```

7、仅升级指定的包

```sh
apt install --only-upgrade 包名
```

8、模拟升级（但不升级任何包）

```sh
apt -s upgrade
```

9、搜索

```sh
apt search 包名
```

10、显示包的详细信息

```sh
apt show 包名
```

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

### 终端美化

终端-点击“三杠”-配置文件首选项

- 文本和背景颜色：Solarized
- 调色板：Solarized
