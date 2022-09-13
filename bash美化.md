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
