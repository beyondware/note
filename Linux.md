## SSH

- 远程拒绝打开外壳通道:错误:未连接，需要启动 SSH

> Remote rejected opening a shell channel: Error: Not connected

### 查看 SSH 状态

```sh
systemctl status sshd
```

> Active: active (running) 表示开启

> Active: inactive (dead) 表示关闭

### 启动 SSH

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

### 查看 SSH 连接状态

```sh
ps -e | grep ssh
```

> 显示 00:00:00 sshd 表示连接上了 SSH

