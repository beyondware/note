## SSH 登录

1、查看是否开启 SSH

```sh
ps -e | grep ssh
```

> 显示 00:00:00 sshd 表示开启了 SSH

2、安装 SSH

```sh
sudo apt install openssh-client
```

```sh
sudo apt install openssh-server
```

或者

```sh
sudo apt install ssh
```

3、查看 SSH 状态

```sh
systemctl status sshd
```

4、启动 SSH

```sh
sudo /etc/init.d/ssh start
```

> 显示 Starting ssh (via systemctl): ssh.service.表示开启 SSH

5、重启 SSH

```sh
sudo service ssh restart
```

6、停止 SSH

```sh
sudo service ssh stop
```

7、开机启动 SSH，修改 SSH 配置文件（ROOT 登录）

```sh
sudo vi /etc/ssh/sshd_config
```

> PermitRootLogin without-password 修改为 PermitRootLogin yes

## 终端设置

> 终端-点击“三杠”-配置文件首选项

- 文本和背景颜色：Solarized
- 调色板：Solarized

## 常用命令

1、安装

```sh
sudo apt install
```

2、卸载

```sh
sudo apt remove
```

```sh
dpkg uninstall
```

- 自动卸载

```sh
sudo apt autoremove
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

4、系统更新

```sh
sudo apt update
```

5、查看可以升级的软件包

```sh
apt list --upgradable
```

6、升级所有可升级包

```sh
sudo apt upgrade
```

- 自动处理依赖项升级包

```sh
apt full-upgrade
```

7、模拟升级（但不升级任何包）

```sh
apt -s upgrade
```

8、仅升级选定的包

```sh
sudo apt --only-upgrade install 包名
```

9、搜索

```sh
apt search 包名
```

10、显示包的详细信息

```sh
apt show 包名
```

## 修改镜像源

```sh
vi /etc/apt/sources.list
```

官方源

> http://archive.ubuntu.com/ubuntu/

阿里云

> https://developer.aliyun.com/mirror/ubuntu

清华大学

> https://mirrors.tuna.tsinghua.edu.cn/help/ubuntu/
