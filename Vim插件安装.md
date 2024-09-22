# vim-plug 安装

> https://github.com/junegunn/vim-plug

1、创建 vim 插件目录

```sh
mkdir -p ~/.vim/autoload
```

2、切换到目录

```sh
cd  ~/.vim/autoload
```

3、下载 vim-plug

```sh
wget https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```

4、创建 vimrc

```sh
vim ~/.vimrc
```

5、添加插件、配置到文件

```sh
call plug#begin('~/.vim/plugged')

" 开屏效果
Plug 'mhinz/vim-startify'

call plug#end()
```

6、配置生效

```sh
:source ~/.vimrc
```

7、安装插件

```sh
:PlugInstall
```

# vim-plug 常用命令

1、安装插件

```sh
:PlugInstall
```

2、删除插件

```sh
:PlugClean
```

3、查看插件状态

```sh
:PlugStatus
```

4、更新 vim-plug

```sh
:PlugUpgrade
```

5、更新所有已安装插件

```sh
:PlugUpdate
```
