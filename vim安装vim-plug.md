### 安装 vim-plug

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
wget https://ghproxy.com/https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```

4、创建 vimrc

```sh
vim ~/.vimrc
```

5、粘贴以下内容

```sh
call plug#begin('~/.vim/plugged')
call plug#end()
```

6、刷新生效

```sh
:source ~/.vimrc
```

### Plug 命令

1、安装插件

```sh
:PlugInstall
```

2、删除插件

```sh
:PlugClean
```

3、更新 vim-plug

```sh
:PlugUpgrade
```

4、查看插件状态

```sh
:PlugStatus
```

5、更新所有已安装插件

```sh
:PlugUpdate
```

6、查看插件信息

```sh
:CocInfo
```
