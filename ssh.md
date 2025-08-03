# 安装 ssh

## Arch

```sh
sudo pacman -S openssh
```

## Debian

```sh
sudo apt install openssh-server
```

## Fedora

```sh
sudo dnf install openssh-server
```

## 验证是否已安装 ssh 服务

```sh
ls /etc | grep ssh
```

# 运行 ssh

> sshd（Arch、Fedora）或者 ssh（Debian），具体情况而定。

## 当前 ssh 状态

```sh
systemctl status ssh
或者
sudo /etc/init.d/ssh status
或者
service ssh status
```

### 报错

> Unit ssh.service could not be found.

```sh
systemctl status sshd
```

Active: active (running) 表示开启

Active: inactive (dead) 表示关闭

## 启动 ssh

```sh
sudo systemctl start ssh
或者
sudo /etc/init.d/ssh start
或者
service ssh start
```

### 报错

> Failed to start ssh.service: Unit ssh.service not found.

```sh
sudo systemctl start sshd
```

## 停止 ssh

```sh
sudo systemctl stop ssh
或者
sudo /etc/init.d/ssh stop
或者
service ssh stop
```

## 重启 ssh

```sh
sudo systemctl restart ssh
或者
sudo /etc/init.d/ssh restart
或者
service ssh restart
```

### 报错

> Failed to restart ssh.service: Unit ssh.service not found.

```sh
sudo systemctl restart sshd
```

## 开机启动 ssh

```sh
sudo systemctl enable ssh
```

### 报错

> Failed to enable unit: Unit ssh.service does not exist

```sh
sudo systemctl enable --now sshd
```

--now：立即执行

## 禁止开机启动 ssh

```sh
sudo systemctl disable ssh
```

# 查看 ssh 进程

```sh
ps -e | grep ssh
```

显示 00:00:00 sshd，已经启动。

# 常见问题

## 错误：未连接

> Remote rejected opening a shell channel: Error: Not connected

1、查看 ssh 状态，是否启动

```sh
systemctl status sshd
```

2、如果未运行，启动 ssh 服务

```sh
sudo systemctl start sshd
```

3、防止重启后，无法连接。开机自启动 ssh

```sh
sudo systemctl enable --now sshd
```

4、如果仍然无法远程连接，是否防火墙阻拦。

方法一、允许 ssh 通过防火墙

```sh
sudo ufw allow ssh
```

方法二、允许 ssh 端口号通过防火墙

查询 ssh 端口号，默认：22

```sh
grep Port /etc/ssh/sshd_config
```

```sh
sudo ufw allow 22/tcp
```

## 身份验证失败

> All configured authentication methods failed

1、编辑

```sh
sudo vim /etc/ssh/sshd_config
```

2、修改（允许密码登录）

```sh
PasswordAuthentication yes（去掉前面#）
```

3、立即自启动 ssh

```sh
sudo systemctl enable --now sshd
```

# ssh 配置

```sh
sudo vim /etc/ssh/sshd_config
```

PermitRootLogin prohibit-password（默认值：禁止密码）/yes/no：允许 root 登录

PermitEmptyPasswords yes/no：允许空密码登录

PasswordAuthentication yes/no：密码验证

PubkeyAuthentication yes/no：密钥验证

# 设置空密码

## 删除用户密码

```sh
passwd -d $USER
```

## 检查用户是否为空密码

```sh
paddwd -S $USER
```

输入结果：Empty password，表示空密码。

## 系统所有空密码的用户

```sh
awk -F ':' '{if($2=="") print $0 }' /etc/shadow
```

