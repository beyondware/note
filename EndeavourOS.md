## 修改 archlinux 镜像源

1、修改

```sh
sudo vim /etc/pacman.d/mirrorlist
```

```sh
## China
Server = https://mirrors.cernet.edu.cn/archlinux/$repo/os/$arch
Server = https://mirror.nju.edu.cn/archlinux/$repo/os/$arch
Server = https://mirrors.tuna.tsinghua.edu.cn/archlinux/$repo/os/$arch
Server = https://mirrors.ustc.edu.cn/archlinux/$repo/os/$arch
Server = https://mirrors.sjtug.sjtu.edu.cn/archlinux/$repo/os/$arch
```

2、更新缓存

```sh
sudo pacman -Syyu
```

3、更新 GPG key

```sh
sudo pacman -S archlinux-keyring
```

## 修改 endeavouros 镜像源

> https://github.com/endeavouros-team/repo

1、修改

```sh
sudo vim  /etc/pacman.d/endeavouros-mirrorlist
```

```sh
## China
Server = https://mirrors.nju.edu.cn/endeavouros/repo/$repo/$arch
Server = https://mirrors.tuna.tsinghua.edu.cn/endeavouros/repo/$repo/$arch
```

2、更新缓存

```sh
sudo pacman -Syyu
```

3、更新 GPG key

```sh
sudo pacman -S endeavouros-keyring
```

## 添加 archlinuxcn 镜像源

> https://repo.archlinuxcn.org/

1、添加

```sh
sudo vim /etc/pacman.conf
```

- 文件末尾添加

```sh
[archlinuxcn]
Server = https://mirrors.cernet.edu.cn/archlinuxcn/$arch
Server = https://mirror.nju.edu.cn/archlinuxcn/$arch
Server = https://mirrors.tuna.tsinghua.edu.cn/archlinuxcn/$arch
Server = https://mirrors.ustc.edu.cn/archlinuxcn/$arch
Server = https://mirror.sjtu.edu.cn/archlinux-cn/$arch
```

2、更新缓存

```sh
sudo pacman -Syyu
```

3、更新 GPG key

```sh
sudo pacman -S archlinuxcn-keyring
```

4、如果遇到一连串error

> https://www.archlinuxcn.org/gnupg-2-1-and-the-pacman-keyring/

- 以 root 账号运行

```sh
pacman -Syu haveged
```

```sh
systemctl start haveged
```

```sh
systemctl enable haveged
```

```sh
rm -fr /etc/pacman.d/gnupg
```

```sh
pacman-key --init
```

```sh
pacman-key --populate archlinux
```

```sh
pacman-key --populate archlinuxcn
```



