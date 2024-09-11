## vim 源码安装

1、安装依赖

```sh
sudo dnf install gcc make ncurses-devel
```

2、克隆 vim 源码

```sh
git clone https://ghproxy.com/https://github.com/vim/vim.git
```

3、切换到 vim/src 目录

```sh
./configure --prefix=/usr/local/vim
```

4、编译和安装

```sh
make && make install
```

## 文件权限

1、查看当前用户 ID

```sh
id --user  #比如：1005
```

2、获取文件所有者

```sh
sudo ls --numeric-uid-gid
```

3、更改文件匹配权限

```sh
sudo chown 1005 文件
```

4、可读可执行权限

```sh
sudo chmod 755 文件
```

或者

```sh
sudo chmod +x 文件
```

## 意外锁屏

1、锁屏

> Ctrl+S

2、解锁

> Ctrl+Q

3、切换`大小写`

> ~

## vim 配置文件

```sh
 ~/.vimrc
```

### 恢复文件

```sh
vim -r 文件名
```

### 强制关闭终端，未正常退出

```sh
ls -a
```

```sh
rm -rf .xxx.swp
```

## 打开文件

1、打开多个文件

```sh
vim 文件名1 文件名2
```

2、打开文件定位到第`n`行

```sh
vim n 文件名
```

3、打开文件定位到`关键词`位置

```sh
vim /关键词 文件名
```

### 显示文件名

> Ctrl+g

或者

```sh
:f
```

## 文件重命名

```sh
:w 新的文件名
```

### 分屏

1、上下分屏

```sh
vim -on 文件名1 文件名2
```

2、左右分屏

```sh
vim -On 文件名1 文件名2
```

```sh
:split 文件名 //水平打开另一个文件

:vsplit 文件名 //垂直打开另一个文件

Ctrl+ww 在“拆分”模式下，不同窗口之间跳转
```

## 保存退出

1、退出

```sh
:q
```

2、强制退出（不会保存）

```sh
:q! 或者 ZQ
```

3、保存

```sh
:w
```

4、保存并退出

```sh
:wq（:x）或者 ZZ
```

5、所有保存并退出

```sh
:wqa（:xa）
```

## 常用操作

```sh
:w（write）保存
:q（quit）退出

u（undo）撤销
Ctrl+R 恢复撤销


增
i/I（insert）插入，I：行首；i：光标前
a/A（append）追加，A：行尾；a：光标后
o/O o：向下插一行；O：向上插一行


删
x 删除一个字符（包括空格）
d（delete） 删除
dd 删除一行
3dd 删除三行
dw（delet word）删除一个单词（包括空格）
diw（delete inner word）删除内部内容
daw（delete around word）
d^ 删除到行首
d$ 删除到行尾

y（yank）复制
yy 复制一行
3yy 复制三行
yiw 复制一个单词
y^ 复制到行首
y$ 复制到行尾

p（paste）粘贴到后
P（大写） 粘贴到前


改
c（change） 改变
ciw（change inner word）删除内部内容，并进入插入模式
ct" 删除双引号里面的内容，并进入插入模式
ct) 删除到右括号，并进入插入模式


查（底线模式）
/ 向后查找
? 向前查找

按一下 n（小写）：向下查找 
按一下 N（大写）：向上查找

f 查找当前行


替
:s/old/new 替换光标位置
:s/old/new/g 替换当前行所有
: 12,15 s/old/new/g 替换12到15行所有
:%s/old/new/g 替换所有


移动
w（word）移动到下一个单词
b（back word）移动到上一个单词

0（数字零）移动到行首
$ 移动到行尾

gg 移动到文件开头
GG 移动到文件结尾

移动到18行 
:18或18G

Ctrl+F（forward：向前）翻到下一页

Ctrl+B（backward：向后）返回上一页

Ctrl+U（upward）

Ctrl+D

Ctrl+O（字母o） 返回到之前位置
```

