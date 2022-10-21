### 分区

```sh
/boot/efi 500M 引导分区
swap 2GB 交换分区
/ 剩余 根目录
```

### 联网

```sh
vim /etc/sysconfig/network-scripts/ifcfg-ens33
```

- ONBOOT=no 改成 yes（正常联网，不用管）

### SSH 登陆

```sh
vim /etc/ssh/sshd_config
```

- PermitRootLogin no 改成 yes

### 修改源

```sh
vi /etc/yum.repos.d/openEuler.repo
```

> http://repo.openeuler.org/

改成（可选）

> https://repo.huaweicloud.com/openeuler/

> https://mirrors.nju.edu.cn/openeuler/

> https://mirrors.tuna.tsinghua.edu.cn/openeuler/

### kiran-desktop 安装

1、更新软件源

```sh
sudo dnf update
```

2、安装 kiran-desktop

```sh
sudo dnf install kiran-desktop
```

3、以图形界面启动

```sh
sudo systemctl set-default graphical.target
```

4、重启系统

```sh
sudo reboot
```
