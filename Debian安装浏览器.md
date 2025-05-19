# Firefox

1、查看

```sh
apt list --installed | grep firefox
```

三个关联包：firefox、firefox-locale-en、firefox-locale-zh-hans

2、删除

```sh
sudo dpkg -P firefox firefox-locale-en firefox-locale-zh-hans
```

# LibreWolf

1、更新并升级系统

```sh
sudo apt update
sudo apt upgrade
```

2、安装所需的依赖

```sh
sudo apt install curl gnupg lsb-release apt-transport-https ca-certificates -y
```

3、导入 LibreWolf 存储库

```sh
curl https://deb.librewolf.net/keyring.gpg | gpg --dearmor \
    | sudo tee /usr/share/keyrings/librewolf.gpg >/dev/null
```

4、导入 GPG 密钥

```sh
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/librewolf.gpg] \
http://deb.librewolf.net $(lsb_release -sc) main" \
    | sudo tee /etc/apt/sources.list.d/librewolf.list
```

5、更新

```sh
sudo apt update
```

6、安装 LibreWolf

```sh
sudo apt install librewolf -y
```

7、启动 LibreWolf

```sh
librewolf
```

8、删除 LibreWolf

```sh
sudo apt remove librewolf
```

9、删除 LibreWolf 存储库

```sh
sudo rm /etc/apt/sources.list.d/librewolf.list
```

10、删除 GPG 密钥

```sh
sudo rm /usr/share/keyrings/librewolf.gpg
```

11、参考

> https://librewolf.net/installation/debian/

# Chromium

1、安装

```sh
sudo apt install chromium-browser
```

2、删除

```sh
sudo apt remove chromium-browser
```

# Chrome

1、下载

```sh
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
```

2、安装

```sh
sudo apt install google-chrome-stable_current_amd64.deb
```

3、删除下载包

```sh
rm google-chrome-stable_current_amd64.deb
```

# Microsoft Edge

1、更新并升级系统

```sh
sudo apt update
sudo apt upgrade
```

2、安装所需的依赖

```sh
sudo apt install software-properties-common apt-transport-https curl ca-certificates -y
```

3、导入 Microsoft Edge APT 存储库

- 下载 GPG 密钥以验证包的真实性

```sh
curl -fSsL https://packages.microsoft.com/keys/microsoft.asc | sudo gpg --dearmor | sudo tee /usr/share/keyrings/microsoft-edge.gpg > /dev/null
```

- 将 Microsoft Edge 存储库添加系统中

```sh
echo 'deb [arch=amd64 signed-by=/usr/share/keyrings/microsoft-edge.gpg] https://packages.microsoft.com/repos/edge stable main' | sudo tee /etc/apt/sources.list.d/microsoft-edge.list
```

4、更新

```sh
sudo apt update
```

5、安装 Microsoft Edge 浏览器


## 稳定版

```sh
sudo apt install microsoft-edge-stable
```

```sh
sudo apt upgrade microsoft-edge-stable
```

```sh
sudo apt remove microsoft-edge-stable
```

```sh
microsoft-edge -version
```

## Beta 版

```sh
sudo apt install microsoft-edge-beta
```

```sh
sudo apt upgrade microsoft-edge-beta
```

```sh
sudo apt remove microsoft-edge-beta
```

```sh
microsoft-edge-beta --version
```

## Dev 版

```sh
sudo apt install microsoft-edge-dev
```

```sh
sudo apt upgrade microsoft-edge-dev
```

```sh
sudo apt remove microsoft-edge-stable-dev
```

```sh
microsoft-edge-dev --version
```

6、删除 Microsoft Edge 所有存储库

```sh
sudo rm -rf /etc/apt/sources.list.d/microsoft*
```

7、删除 Microsoft Edge 密钥

```sh
sudo rm -rf /etc/apt/trusted.gpg.d/microsoft*
sudo rm -rf /usr/share/keyrings/microsoft*
```

## 存储库

> https://packages.microsoft.com/repos/edge/pool/main/m/
