### Parrot 风格美化

1、编辑

```sh
sudo vim ~/.bashrc
```

2、添加

```sh
PS1='\[\033[0;31m\]\342\224\214\342\224\200$([[ $? != 0 ]] && echo "[\[\033[0;31m\]\342\234\227\[\033[0;37m\]]\342\224\200")[\[\033[0;39m\]\u\[\033[01;33m\]@\[\033[01;96m\]\h\[\033[0;31m\]]\342\224\200[\[\033[0;32m\]\w\[\033[0;31m\]]\n\[\033[0;31m\]\342\224\224\342\224\200\342\224\200\342\225\274 \[\033[0m\]\[\e[01;33m\]\$\[\e[0m\]'
```

3、刷新生效

```sh
source ~/.bashrc
```

### bash-it 命令补全（推荐）

> https://github.com/Bash-it/bash-it

1、克隆

```sh
git clone --depth=1 https://ghproxy.com/https://github.com/Bash-it/bash-it.git ~/.bash_it
```

2、脚本安装

```sh
~/.bash_it/install.sh
```

3、刷新生效

```sh
source ~/.bashrc
```

### powerline 状态行

> https://wiki.archlinux.org/title/Powerline

> https://powerline.readthedocs.io/en/latest/index.html

> https://github.com/powerline/powerline

1、安装依赖

```sh
sudo pacman -S python-pip git
```

2、安装powerline

- 可能不是最新版（注意：安装powerline-status，而不是powerline）

```sh
pip install powerline-status
```

- 网络环境原因（不推荐）

```sh
pip install git+git://github.com/powerline/powerline
```

3、下载系统字体及字体配置文件

```sh
wget https://ghproxy.com/https://github.com/powerline/powerline/raw/develop/font/PowerlineSymbols.otf
```

```sh
wget https://ghproxy.com/https://github.com/powerline/powerline/raw/develop/font/10-powerline-symbols.conf
```

4、将系统字体移到字体目录

```sh
mv PowerlineSymbols.otf /usr/share/fonts/
```
5、更新系统的字体缓存

```sh
fc-cache -vf /usr/share/fonts/
```

6、移动字体配置文件

```sh
mv 10-powerline-symbols.conf /etc/fonts/conf.d/
```

7、bash配置powerline

```sh
vim ~/.bashrc
```

- 添加

```sh
export TERM="screen-256color"
```

8、bash默认打开powerline配置

- 先获取powerline安装路径

```sh
pip show powerline-status
```

- 获取地址（后面会用到）

```sh
/usr/lib/python3.10/site-packages
```

- 编辑

```sh
vim ~/.bashrc
```

- 添加

```sh
powerline-daemon -q
POWERLINE_BASH_CONTINUATION=1
POWERLINE_BASH_SELECT=1
. /usr/lib/python3.10/site-packages/powerline/bindings/bash/powerline.sh
```

9、退出终端，重新打开生效。

10、vim配置powerline

```sh
vim ~/.vimrc
```

- 添加

```sh
set rtp+=/usr/lib/python3.10/site-packages/powerline/bindings/vim/
set laststatus=2
set t_Co=256
```
