### 安装 snapd

1、Ubuntu

```sh
sudo apt update
```

```sh
sudo apt install snapd
```

2、Fedora

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

2、卸载

```sh
sudo snap remove 软件名
```

3、更新

```sh
sudo snap refresh 软件名
```

- 指定通道版本

```sh
sudo snap refresh 软件名 channel=latest/stable
```

```sh
sudo killall 软件名
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

### 报错信息

> cannot find signatures with metadata for snap

- 解决方法

> 任何未通过 Snap 商店分发的 Snap 包都必须使用 --dangerous 选项进行安装

```sh
sudo snap install --dangerous
```

### 参考文档

> https://snapcraft.io/docs/installing-snapd

> https://snapcraft.io/store
