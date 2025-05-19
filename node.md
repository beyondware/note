## 官方存储库

> https://nodejs.org/en/download/package-manager

### Ubuntu

```sh
sudo apt update && sudo apt upgrade
```

```sh
sudo apt install nodejs
```

### Fedora

```sh
sudo dnf install nodejs
```

## NodeSource 存储库

1、导入 NodeSource 存储库

### 每日构建版

```sh
curl -fsSL https://deb.nodesource.com/setup_current.x | sudo -E bash -
```

### 长期支持版

```sh
curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash -
```

2、安装 Node.js

```sh
sudo apt install nodejs
```

3、检查版本

```sh
node --version
```

## nvm 版本管理器

> https://github.com/nvm-sh/nvm

1、安装 nvm

```sh
wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/master/install.sh | bash
```

2、重新启动终端或运行加载 nvm

```sh
source ~/.bashrc
```

3、列出

### 可安装 Node.js 版本

```sh
nvm ls-remote
```

###  Node.js LTS 版本

```sh
nvm ls-remote --lts
```

4、安装

```sh
nvm install 版本号（例如：v16.16.0）
```

5、删除

```sh
nvm uninstall 版本号（例如：v16.16.0）
```

6、查看版本

```sh
node --version
```

```sh
npm --version
```

7、列出已安装

```sh
nvm ls
```

8、切换

### 指定版本

```sh
nvm alias default 版本号
```

### 临时版本

```sh
nvm use 版本号
```

## 源码安装

> https://nodejs.org/zh-cn/download/

1、切换到 root 账号

```sh
cd /usr/local
```

2、下载 node

```sh
wget https://nodejs.org/dist/v16.16.0/node-v16.16.0-linux-x64.tar.xz
```

3、解压 node

```sh
tar -Jxvf node-v16.16.0-linux-x64.tar.xz
```

4、 建立软链接，全局引用

```sh
ln -s /usr/local/node-v16.16.0-linux-x64/bin/node /usr/local/bin/node
```

```sh
ln -s /usr/local/node-v16.16.0-linux-x64/bin/npm /usr/local/bin/npm
```

5、验证

```sh
node --version
```

```sh
npm --version
```
