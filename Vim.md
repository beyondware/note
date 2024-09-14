## 源码安装

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

## 文件赋予权限（可读可执行）

```sh
sudo chmod 755 文件
```

或者

```sh
sudo chmod +x 文件
```

## 强制关闭终端

### 恢复

```sh
vim -r 文件
```

### 删除

```sh
ls -a
```

```sh
rm -rf .文件.swp
```

## 锁屏

1、锁屏

Ctrl+S

2、解锁

Ctrl+Q

3、切换`大小写`

~

## 用户配置文件

```sh
sudo vim ~/.vimrc
```

## 打开

1、打开多个文件

```sh
vim 文件名1 文件名2
```

2、打开文件定位到第`n`行

```sh
vim n 文件名
```

3、打开文件并定位到`关键词`位置

```sh
vim /关键词 文件名
```

## 显示文件名

Ctrl+G

或者

```sh
:f
```

## 另存为

```sh
:w 新的文件
```

## 分屏

1、上下分屏

```sh
vim -on 文件1 文件2
```

2、左右分屏

```sh
vim -On 文件1 文件2
```

```sh
:split 文件 //水平打开另一个文件

:vsplit 文件 //垂直打开另一个文件
```

Ctrl+W 在“拆分”模式下，不同窗口之间跳转


## 保存退出

1、退出

```sh
:q（quit：退出）
```

2、强制退出（不会保存）

```sh
:q! 或者 ZQ
```

3、保存

```sh
:w（write：写入）
```

4、保存并退出（先按W再按Q）

```sh
:wq（:x）或者 ZZ
```

5、所有保存并退出

```sh
:wqa（:xa）
```

## 移动

移动到第18行

```sh
:18+回车键 或 18G
```

gg 移动到文件开头
GG 移动到文件结尾

```sh
w（word）      移动到下一个单词
b（back word） 移动到上一个单词

0（数字零） 移动到行首（相当于按键【Home】）
$          移动到行尾（相当于按键【End】）

Ctrl+O（字母O）          返回到之前光标位置

Ctrl+F（forward：向前）  向下翻一页（相当于按键【Page Down】）
Ctrl+B（backward：向后） 向上翻一页（相当于按键【Page Up】）

Ctrl+D   向下翻半页
Ctrl+U   向上翻半页
```

## 撤销

u（undo）撤销

Ctrl+R 恢复撤销

## 复制

```sh
y（yank）复制

yy 复制一行
3yy 复制三行

yiw 复制一个单词

y^ 复制到行首
y$ 复制到行尾
```

## 粘贴

```sh
p（paste）  粘贴到后
P（大写）   粘贴到前
```

## 增

```sh
i/I（insert）插入
I：行首；i：光标前

a/A（append）追加
A：行尾；a：光标后

o/O（字母O）
o：向下插一行；O（大写字母O）：向上插一行
```

## 删

```sh
x 删除一个字符（包括空格）
d（delete） 删除

dd  删除一行
3dd 删除三行

dw（delet word）删除一个单词（包括空格）
diw（delete inner word）删除内部内容
daw（delete around word）

d^ 删除到行首
d$ 删除到行尾
```

## 改

```sh
c（change） 改变
ciw（change inner word）删除内部内容，并进入插入模式
ct" 删除双引号里面的内容，并进入插入模式
ct) 删除到右括号，并进入插入模式
```

## 查（底线模式+回车键）

### 向后查找

```sh
/搜索词+回车键

按一下 n（小写）：向下查找 
按一下 N（大写）：向上查找
```

### 向前查找

```sh
?搜索词+回车键

刚好相反
按一下 n（小写）：向上查找 
按一下 N（大写）：向下查找
```

## 替（底线模式+回车键）

```sh
:s/old/new     替换当前光标位置
:s/old/new/g   替换当前行所有
:%s/old/new/g  替换所有

:12,15 s/old/new/g 替换12到15行所有
```



