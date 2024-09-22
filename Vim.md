## 模式

### 退回普通模式（按【Esc】键 或者 Ctrl + C）

> Normal

### 插入模式

> 底部出现-- INSERT --字样

### 可视化模式

按 v （小写）

> 底部出现-- VISUAL --字样

### 可视化行模式

按 V （大写）

> 底部出现-- VISUAL LINE --字样

### 可视化块模式

Ctrl+V

> 底部出现-- VISUAL BLOCK --字样

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

## E32：No file name

```sh
:w 文件名
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

## 锁屏与解锁

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

## 配置生效

```sh
source ~/.vimrc
```

### 显示行号

```sh
:set number 或者简化 :set nu
```

```sh
:set nonumber 或者简化 :set nonu
```

### 设置 hybird 主题

```sh
:colorscheme hybird
```

### 显示语法高亮

```sh
:syntax on
```

### 搜索高亮显示

```sh
:set hlsearch
```

### 自动保存

```sh
:set autowrite
```

### vim 与系统剪贴板之间来回复制粘贴

```sh
:set clipboard=unnamed
```

### 按 F2 进入粘贴模式（映射）

```sh
:set pastetoggle=<F2>
```

### 粘贴模式（防止粘贴时乱码）

```sh
:set paste
```

```sh
:set nopaste
```

### 自动缩进

```sh
:set autoindent
```

### 替换前，需确认

```sh
:set confirm
```

### 忽略大小写（默认区分大小写）

```sh
:set  ignorecase
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

## 底部显示文件名

Ctrl+G

或者

```sh
:f
```

## 文件另存为

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

3、分屏

```sh
:sp 文件       ##水平打开另一个文件（:split） 水平分屏
:vs 文件       ##垂直打开另一个文件（:vsplit）垂直分屏（vertical split）
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

```sh
:18+回车键 或 18G  ##移动到第18行
```
```sh
gg 移动到文件开头
GG 移动到文件结尾（最后一行）
:$（相当于 GG）
```

Ctrl+方向键：相对于【方向键】加速移动

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

j（jump：跳转）

f（find：查找）

t（till：直达）
```

## 撤销

u（undo）              撤销

Ctrl+R（redo：恢复）   恢复撤销

## 剪切（删除）

d：效果同一样，都用d

## 复制（openrator + motion = action）

```sh
y（yank）复制

yy   复制一行（当前行）
3yy  复制三行

yiw  复制一个单词

y^   复制到行首
y$   复制到行尾
```

## 粘贴

```sh
p（paste）  粘贴到后
P（大写）   粘贴到前
```

## 增（插入）

```sh
i/I（insert）插入
I：行首；i：光标前


a/A（append）追加
A：行尾；a：光标后


o/O（open a line：另起一行）
o：                             另起一行，向下插一行；
O（大写字母O）：                 另起一行，向上插一行。
```

## 删（openrator + motion = action）

```sh
x 删除一个字符（包括空格）
d（delete） 删除

dd    删除一行（当前行）
3dd   删除三行

dw（delet word）          删除一个单词（包括空格）
diw（delete inner word）  删除内部内容

d^   删除到行首
d$   删除到行尾
```

## 改

```sh
c（change） 改变
ciw（change inner word）删除内部内容，并进入插入模式
ct"   删除双引号里面的内容，并进入插入模式
ct)   删除到右括号，并进入插入模式
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
:s/old/new          替换当前光标位置
:s/old/new/g        替换当前行所有

:% s/old/new/g      替换所有
:12,15 s/old/new/g  替换12到15行所有
```

### 全文（内容）

```sh
:%
```

### 清空全文

```sh
:%d
```

## 全选复制

1、为确保当前处于普通模式，可以按一下`Esc键`。

2、使用 ggVG 选择整个文件内容

```sh
gg： 将光标移动文件开头
V：  进入可视化行模式
G：  将移动光标文件结尾
```

3、按 y 复制选中的内容

4、移动到粘贴位置，按 p 粘贴

## 参考

> https://vim80.readthedocs.io/zh/latest/index.html

## 寄存器

"register 指定寄存器，不指定默认为无名寄存器

```sh
"a+yy            ##复制一行到 a 寄存器
"b+dd            ##删除一行到 b 寄存器

:reg a           ##查看寄存器 a 里面的内容
:reg b           ##查看寄存器 b 里面的内容

"a+p             ##调用寄存器 a，按 p 在粘贴
```

### 专用寄存器

```sh
"0+y              ##按 y 复制文本，同时会复制到寄存器0
```

### 系统剪贴板

```sh
"+                  ##按 y 复制到系统剪贴板
                    ##在系统复制好后，"+p 粘贴到 vim，不会格式乱码
```

