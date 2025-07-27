# SSH

## 未安装 SSH 报错

```sh
Unit sshd.service could not be found.
```

## 安装 SSH

### Arch

```sh
sudo pacman -S openssh
```

### Debian

```sh
sudo apt install openssh-server
```

### Fedora

```sh
sudo dnf install openssh-server
```

## 验证是否已安装 SSH 服务

```sh
ls /etc | grep ssh
```

# 运行 SSH

sshd（Arch、Fedora）或者 ssh（Debian），具体情况而定。

## 当前 SSH 状态

```sh
systemctl status ssh
或者
sudo /etc/init.d/ssh status
或者
service ssh status
```

> Active: active (running) 表示开启

> Active: inactive (dead) 表示关闭

## 启动 SSH

```sh
sudo systemctl start ssh
或者
sudo /etc/init.d/ssh start
或者
service ssh start
```

### 报错

```sh
Failed to start ssh.service: Unit ssh.service not found.
```

```sh
sudo systemctl start sshd
```

## 停止 SSH

```sh
sudo systemctl stop ssh
或者
sudo /etc/init.d/ssh stop
或者
service ssh stop
```

## 重启 SSH

```sh
sudo systemctl restart ssh
或者
sudo /etc/init.d/ssh restart
或者
service ssh restart
```

### 报错

```sh
Failed to restart ssh.service: Unit ssh.service not found.
```

```sh
sudo systemctl restart sshd
```

## 开机启动 SSH

```sh
sudo systemctl enable --now ssh
```

--now：立即执行

### 报错

```sh
Failed to enable unit: Unit ssh.service does not exist
```

```sh
sudo systemctl enable sshd
```

## 禁止开机启动 SSH

```sh
sudo systemctl disable ssh
```

## 查看 SSH 进程

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

修改成

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

## 如果仍然无法远程连接

允许 ssh 通过防火墙

```sh
sudo ufw allow ssh
```
