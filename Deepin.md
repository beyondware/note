### 模式切换

> Win+Shift+Tab

### SSH

1、安装 SSH

```sh
sudo apt install openssh-server
```

2、启动 SSH

```sh
sudo /etc/init.d/ssh start
```

或者

```sh
sudo systemctl start ssh
```

3、开机启动 SSH

```sh
sudo systemctl enable ssh
```

4、修改 SSH 允许远程登陆

```sh
sudo vim /etc/ssh/sshd_config
```

- 修改成

```sh
PermitRootLogin yes
```

### 修改源

1、编辑

```sh
sudo vim /etc/apt/sources.list
```

- 文件最前面添加以下内容

```sh
deb [by-hash=force] https://mirrors.nju.edu.cn/deepin/ apricot main contrib non-free
```

2、更新

```sh
sudo apt update
```

3、参考源

> https://developer.aliyun.com/mirror/deepin
