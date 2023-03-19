## 安装桌面环境

1、组列出

```sh
dnf group list
```

2、组安装

```sh
dnf groupinstall "Server with GUI"
```

3、开启图形化

```sh
systemctl set-default graphical
```

4、组移除

```sh
dnf groupremove "Server with GUI"
```

## 镜像源

1、替换

```sh
sudo sed -e 's|^mirrorlist=|#mirrorlist=|g' \
         -e 's|^#baseurl=http://dl.rockylinux.org/$contentdir|baseurl=https://mirrors.cernet.edu.cn/rocky|g' \
         -i.backup \
         /etc/yum.repos.d/rocky-extras.repo \
         /etc/yum.repos.d/rocky.repo
```

2、生成缓存

```sh
sudo dnf makecache
```

3、参考

> https://help.mirrors.cernet.edu.cn/rocky/

