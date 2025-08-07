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

# Chromium

1、安装

```sh
sudo apt install chromium-browser
```

2、删除

```sh
sudo apt remove chromium-browser
```
