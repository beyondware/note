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

1、安装

```sh
sudo snap install 软件名
```

- 安装 snap-store（可选）

```sh
sudo snap install snap-store
```

2、移除

```sh
sudo snap remove 软件名
```

3、更新

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

4、运行

```sh
snap run 软件名
```

5、启用 snap

```sh
sudo snap enable
```

6、禁用 snap

```sh
sudo snap disable
```

7、查找某一命令帮助

```sh
snap help 命令
```

8、查找要安装的软件

```sh
snap find 软件名
```

9、查找要安装的软件详细信息

```sh
snap info 软件名
```

10、列出已安装软件

```sh
snap list
```

11、下载某到本地

```sh
snap download 软件名
```

12、指定目录打包成 snap

```sh
sudo snap pack
```

13、安装位置

> /var/lib/snapd/snaps

14、删除所有旧版本的快照

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

15、清理缓存文件

```sh
sudo rm -rf /var/lib/snapd/cache/*
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
