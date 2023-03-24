## 修改 arch 镜像源

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

## 修改 endeavouros 镜像源

https://github.com/endeavouros-team/repo

```sh
sudo vim  /etc/pacman.d/endeavouros-mirrorlist
```

```sh
Server = https://mirrors.nju.edu.cn/endeavouros/repo/$repo/$arch
Server = https://mirrors.tuna.tsinghua.edu.cn/endeavouros/repo/$repo/$arch
Server = https://mirror.linux.pizza/endeavouros/repo/$repo/$arch
```
