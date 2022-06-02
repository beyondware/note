## python 自定义安装

1、选择“Customize installation”（自定义安装）

2、一定要勾选“Add Python to PATH”（添加到环境变量)

3、高级选项：勾选“Install for users”（所有人可用）

> 显示“Setup was successful”（表示安装成功）

4、验证结果

```sh
python --version
```

```sh
pip --version
```

## 解决 python 没有安装 pip 的问题

- 一般 Linux 自带 python，但是没有安装 pip 报错

```sh
Failed to find python3-pip;21.3.1-2.fc36;noarch;fedora
```

- 解决方法

```sh
python -m ensurepip --upgrade
```

```sh
python -m pip install --upgrade pip
```

## 换镜像源

```sh
pip install pip -U
```

- 永久性，以**南京大学**镜像源为例：

```sh
pip config set global.index-url https://mirror.nju.edu.cn/pypi/web/simple
```

## PyCharm

> https://www.jetbrains.com/pycharm/
