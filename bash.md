# shell

## 查看当前 shell

```sh
echo $SHELL
或者
echo $0
或者
ps -p $$
```

## 列出已安装 shell

```sh
cat /etc/shells
```

## 设置 bash 为默认 shell

```sh
sudo chsh -s /bin/bash
```

退出终端，重开才能生效。

## 如果执行不生效

```sh
sudo usermod -s /bin/bash $USER
```

# 历史记录

## 删除 bash 历史记录

```sh
cat /dev/null > ~/.bash_history && history -c && exit
```

## 擦拭历史记录

```sh
sudo pacman -S wipe
```

执行

```sh
wipe ~/.bash_history
```

# powerline 安装

## 安装依赖

```sh
sudo pacman -S python-pip git
```

## pip 安装 powerline-status

```sh
pip install powerline-status
```

## powerline 源码安装

1、克隆到本地

```sh
git clone https://github.com/powerline/powerline.git
```

2、切换到 powerline 目录

```sh
cd powerline/
```

3、执行安装

```sh
pip install .
或者
python setup.py install
```

## 下载系统字体及字体配置文件

```sh
wget https://github.com/powerline/powerline/raw/develop/font/PowerlineSymbols.otf
```

```sh
wget https://github.com/powerline/powerline/raw/develop/font/10-powerline-symbols.conf
```

将系统字体移到字体目录

```sh
sudo mv PowerlineSymbols.otf /usr/share/fonts/
```

更新字体缓存

```sh
fc-cache -vf /usr/share/fonts/
```

移动字体配置文件

```sh
sudo mv 10-powerline-symbols.conf /etc/fonts/conf.d/
```

## bash 默认打开 powerline 配置

1、先获取 powerline 安装路径

```sh
pip show powerline-status
```

获取地址（后面会用到，每个人安装路径不一样）

```sh
/usr/lib/python3.10/site-packages
```

2、编辑配置文件

```sh
vim ~/.bashrc
```

添加

```sh
powerline-daemon -q
POWERLINE_BASH_CONTINUATION=1
POWERLINE_BASH_SELECT=1
. /usr/lib/python3.10/site-packages/powerline/bindings/bash/powerline.sh
```

3、刷新

```sh
source ~/.bashrc
```

## vim 配置 powerline

```sh
vim ~/.vimrc
```

添加

```sh
set rtp+=/usr/lib/python3.10/site-packages/powerline/bindings/vim/
set laststatus=2
set t_Co=256
```

## 参考

> https://wiki.archlinux.org/title/Powerline

> https://powerline.readthedocs.io/en/stable/

> https://github.com/powerline/powerline

# Parrot 风格

## 全局

1、查看配置文件

```sh
ls /etc | grep bash
```

2、编辑 bash 配置文件

```sh
sudo vim /etc/bashrc
或者
sudo vim /etc/bash.bashrc
```

3、替换（if 两处 PS1）

```sh
    PS1="\[\033[0;31m\]\342\224\214\342\224\200\$([[ \$? != 0 ]] && echo \"[\[\033[0;37m\]\342\234\227\[\033[0;31m\]]\342\224\200\")[$(if [[ ${EUID} == 0 ]]; then echo '\[\033[01;31m\]root\[\033[01;33m\]@\[\033[01;96m\]\h'; else echo '\[\033[0;39m\]\u\[\033[01;33m\]@\[\033[01;96m\]\h'; fi)\[\033[0;31m\]]\342\224\200[\[\033[0;32m\]\w\[\033[0;31m\]]\n\[\033[0;31m\]\342\224\224\342\224\200\342\224\200\342\225\274 \[\033[0m\]\[\e[01;33m\]\\$\[\e[0m\]"
```

4、退出终端，重新打开终端查看配置结果。

```sh
echo "$PS1" 
```

## 用户

1、编辑

```sh
sudo vim ~/.bashrc
```

2、替换（if 两处 PS1）

```sh
    PS1="\[\033[0;31m\]\342\224\214\342\224\200\$([[ \$? != 0 ]] && echo \"[\[\033[0;37m\]\342\234\227\[\033[0;31m\]]\342\224\200\")[$(if [[ ${EUID} == 0 ]]; then echo '\[\033[01;31m\]root\[\033[01;33m\]@\[\033[01;96m\]\h'; else echo '\[\033[0;39m\]\u\[\033[01;33m\]@\[\033[01;96m\]\h'; fi)\[\033[0;31m\]]\342\224\200[\[\033[0;32m\]\w\[\033[0;31m\]]\n\[\033[0;31m\]\342\224\224\342\224\200\342\224\200\342\225\274 \[\033[0m\]\[\e[01;33m\]\\$\[\e[0m\]"
```

3、刷新（部分系统，可能不会生效）

```sh
source ~/.bashrc
```
