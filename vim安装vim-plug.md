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

### vimrc 配置

```sh
" github镜像
let g:plug_url_format = 'git@hub.fastgit.xyz/%s.git'
"

" 彩虹插件配置生效
let g:rainbow_active = 1 "0 if you want to enable it later via :RainbowToggle
"

" 代码补全
let g:apc_enable_ft = {'*':1}
"


call plug#begin('~/.vim/plugged')

" 彩虹括号
Plug 'luochen1990/rainbow'
"

" 历史记录
Plug 'mhinz/vim-startify'
"

" 轻量级代码补全
Plug 'skywind3000/vim-auto-popmenu'
Plug 'skywind3000/vim-dict'
"

call plug#end()

```

### 解决 github 无法链接

在`vim ~/.vim/autoload/plug.vim`修改两处

```sh
let fmt = get(g:, 'plug_url_format', 'https://git::@github.com/%s.git')
```

改成

```sh
let fmt = get(g:, 'plug_url_format', 'https://git::@hub.fastgit.xyz/%s.git')
```

```sh
\ '^https://git::@github\.com', 'https://github.com', '')
```

改成

```sh
\ '^https://git::@hub.fastgit\.xyz', 'https://hub.fastgit.xyz', '')
```
