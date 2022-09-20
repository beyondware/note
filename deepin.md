### 模式切换

> Win+Shift+Tab

### ssh 登陆

1、安装ssh

```sh
sudo apt install openssh-server
```

2、启动ssh

```sh
sudo /etc/init.d/ssh start
```

或者

```sh
sudo systemctl start ssh
```

3、开机启动ssh

```sh
sudo systemctl enable ssh
```

4、修改ssh允许登陆

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

### apt 命令

```sh
apt 2.5.2 (amd64)
用法： apt [选项] 命令

命令行软件包管理器 apt 提供软件包搜索，管理和信息查询等功能。
它提供的功能与其他 APT 工具相同（像 apt-get 和 apt-cache），
但是默认情况下被设置得更适合交互。

常用命令：
  list - 根据名称列出软件包
  search - 搜索软件包描述
  show - 显示软件包细节
  install - 安装软件包
  reinstall - 重新安装软件包
  remove - 移除软件包
  autoremove - 卸载所有自动安装且不再使用的软件包
  update - 更新可用软件包列表
  upgrade - 通过 安装/升级 软件来更新系统
  full-upgrade - 通过 卸载/安装/升级 来更新系统
  edit-sources - 编辑软件源信息文件
  satisfy - 使系统满足依赖关系字符串

参见 apt(8) 以获取更多关于可用命令的信息。
程序配置选项及语法都已经在 apt.conf(5) 中阐明。
欲知如何配置软件源，请参阅 sources.list(5)。
软件包及其版本偏好可以通过 apt_preferences(5) 来设置。
关于安全方面的细节可以参考 apt-secure(8).
                                         本 APT 具有超级牛力。
```
