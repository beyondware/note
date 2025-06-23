# SSH

## 报错

> Unit sshd.service could not be found.

## Debian

```sh
sudo apt install openssh-server
```

## Fedora

```sh
sudo dnf install openssh-server
```

## Arch

```sh
sudo pacman -S openssh
```

# 运行 SSH

sshd（Fedora）或者 ssh（Debian），具体情况而定。

1、当前 SSH 状态

```sh
systemctl status ssh 或者 sudo /etc/init.d/ssh status 或者 service sshd status
```

> Active: active (running) 表示开启

> Active: inactive (dead) 表示关闭

2、启动 SSH

```sh
sudo systemctl start ssh 或者 sudo /etc/init.d/ssh start 或者 service sshd start
```

3、停止 SSH

```sh
sudo systemctl stop ssh 或者 sudo /etc/init.d/ssh stop 或者 service sshd stop
```

4、重启 SSH

```sh
sudo systemctl restart ssh 或者 sudo /etc/init.d/ssh restart 或者 service sshd restart
```

5、开机启动 SSH

```sh
sudo systemctl enable ssh
```

6、禁止开机启动 SSH

```sh
sudo systemctl disable ssh
```

# 查看 SSH 进程

```sh
ps -e | grep ssh
```

显示 00:00:00 sshd，已经启动。

# 登陆 SSH

## 报错一

> Remote rejected opening a shell channel: Error: Not connected

1、编辑

```sh
sudo vim /etc/ssh/sshd_config
```

2、修改

```sh
# PermitRootLogin prohibit-password
```

改成

```sh
PermitRootLogin yes
```

3、重启 ssh

```sh
sudo systemctl restart ssh
```

## 报错二

> All configured authentication methods failed

1、编辑

```sh
sudo vim /etc/ssh/sshd_config
```

2、修改

```sh
PasswordAuthentication yes（去掉前面#）
```

3、重启 ssh

```sh
sudo systemctl restart ssh
```
