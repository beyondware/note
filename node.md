## 直接安装

### Ubuntu

```sh
sudo apt install nodejs
```

### Fedora

```sh
sudo dnf install nodejs
```

## nvm 安装

> https://github.com/nvm-sh/nvm

1、安装 nvm

```sh
wget -qO- https://ghproxy.com/https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
```

- 安装后，需退出终端，重新进入。

2、列出可安装 node 版本

```sh
nvm ls-remote
```

- 列出可安装 LTS 版本

```sh
nvm ls-remote --lts
```

3、安装 node

- 最新 LTS 版本

```sh
nvm install --lts
```

- 指定版本

```sh
nvm install 版本号（例如：v16.16.0）
```

4、删除 node

```sh
nvm uninstall 版本号（例如：v16.16.0）
```

5、查看 node 版本

```sh
node --version
```

```sh
npm --version
```

6、列出已安装 node 版本

```sh
nvm ls
```

7、切换 node 版本

- 指定版本

```sh
nvm alias default 版本号
```

- 临时版本

```sh
nvm use 版本号
```

## 源码安装（root 账号）

> https://nodejs.org/zh-cn/download/

1、root 账号，切换到

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
