### 安装 snapd

#### Ubuntu

```sh
sudo apt update
```

```sh
sudo apt install snapd
```

#### Fedora

```sh
sudo dnf install shapd
```

### 常用命令

#### 安装

```sh
sudo snap install 软件名
```

- 安装 snap-store（可选）

```sh
sudo snap install snap-store
```

##### 列出已安装软件

```sh
snap list
```

#### 移除

```sh
sudo snap remove 软件名
```

#### 更新

- 先杀死进程

```sh
sudo killall 软件名
```

- 在更新软件

```sh
sudo snap refresh 软件名
```

- 指定通道版本

```sh
sudo snap refresh 软件名 channel=latest/stable
```

#### 禁止更新

1、永久禁用 snap 软件包自动更新

```sh
snap refresh --hold
```

2、临时禁用 snap 软件包自动更新（如：48小时）

```sh
snap refresh --hold=48h
```

#### 运行

```sh
snap run 软件名
```

#### 启用 snap

```sh
sudo snap enable
```

#### 禁用 snap

```sh
sudo snap disable
```

#### 帮助

```sh
snap help 命令
```

#### 查找

```sh
snap find 软件名
```

#### 详细信息

```sh
snap info 软件名
```

#### 下载到本地

```sh
snap download 软件名
```

#### 安装位置

> /var/lib/snapd/snaps

#### 删除所有旧版本的快照

- 清理 Snap 脚本，例如：clean_snap.sh

```sh
#!/bin/bash
# Removes old revisions of snaps
# CLOSE ALL SNAPS BEFORE RUNNING THIS
set -eu

LANG=C snap list --all | awk '/disabled/{print $1, $3}' |
    while read snapname revision; do
        snap remove "$snapname" --revision="$revision"
    done
```

- 提权

```sh
chmod +x clean_snap.sh
```

- 运行

```sh
sudo ./clean_snap.sh
```

#### 清理缓存文件

```sh
sudo rm -rf /var/lib/snapd/cache/*
```

#### 指定目录打包成 snap

```sh
sudo snap pack
```

### 报错信息

> cannot find signatures with metadata for snap

- 解决方法
 
> 任何未通过 Snap 商店分发的 Snap 包都必须使用 --dangerous 选项进行安装

```sh
sudo snap install 软件包.snap --dangerous
```

### 参考文档

> https://snapcraft.io/docs/installing-snapd

> https://snapcraft.io/store

### snap help

```sh
snap 命令允许您安装、配置、刷新和删除 snap。Snap 是跨许多不同 Linux 发行版工作的软件包（类型），可实现最新应用程序和实用程序的安全交付和操作。

用法：snap <命令> [<选项>...]

常用的命令可以分类如下：

             基本信息: find, info, install, remove, list
            ...更多: refresh, revert, switch, disable, enable, create-cohort
               历史: changes, tasks, abort, watch
             守护程序: services, start, stop, restart, logs
               权限: connections, interface, connect, disconnect
               配置: get, set, unset, wait
             应用别名: alias, aliases, unalias, prefer
               帐号: login, logout, whoami
               快照: saved, save, check-snapshot, restore, forget
               设备: model, reboot, recovery
               开发: download, pack, run, try
     Quota Groups: set-quota, remove-quota, quotas, quota
  Validation Sets: validate
        ... Other: warnings, okay, known, ack, version

请运行 'snap help <命令>' 来获得该命令的更多信息。
请运行 'snap help -all' 来获得所有命令的短摘要。
```
