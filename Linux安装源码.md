### 下载

```sh
wget 下载链接
```

### 解压软件包

```sh
tar -zxvf 下载包.tar.gz
```

```sh
tar -jxvf 下载包.tar.bz2
```

```sh
tar -zxJf 下载包.tar.xz
```

### 进入包目录

```sh
cd 包目录
```

- 查看源代码中是否有`configure`或者`Makefile`文件

### 执行 configure

- 执行 configure 指定安装路径

```sh
./configure --prefix=/usr/local/包名
```

- 正确执行后，会生成`Makefile`文件

> creating objs/Makefile //显示结果

### 缺少依赖

> 缺少 xxx library，报错

```sh
sudo dnf install xxx xxx-devel
```

### 报错清理

```sh
make clean
```

- 需要删除 Makefile 和 objs 文件

```sh
rm -rf Makefile objs
```

### 再执行 configure

- 执行 configure 指定安装路径

```sh
./configure --prefix=/usr/local/包名
```

### 检验上一步操作是否正确

```sh
echo &?
```

### 编译 Makefile 文件

```sh
make -j4  //4线程
```

### 安装

```sh
sudo make install
```

### 卸载

```sh
sudo make uninstall
```

### 使用软件

- 安装成功后，一般进入下面路径，来启动、停止等操作。

> /usr/local/包名/sbin

- 如果启动失败，需要关闭防火墙

```sh
systemctl stop firewalld
```

1、启动

```sh
./包名
```

2、停止

```sh
./包名 -s stop
```

3、重新加载

```sh
./包名 -s reload
```
