## 基础

1、锁屏

> Ctrl+s

2、解锁

> Ctrl+q

3、切换`大小写`

> ~

### vim 配置文件

```sh
 ~/.vimrc
```

1、恢复上一次打开文件

```sh
vim -r 文件名
```

2、强制关闭终端，未正常退出（**重点**）

```sh
rm -rf .xxx.swp
```

### 打开

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

### 显示当前文件名

> Ctrl+g

或者

```sh
:f
```

### 分屏打开

1、上下分屏

```sh
vim -on 文件名1 文件名2
```

2、左右分屏

```sh
vim -On 文件名1 文件名2
```

## INSERT 模式

- 在`普通模式`下，按`i`插入

光标之`前`输入：i

光标之`后`输入：a

本行`开头`位置输入：I

本行`结尾`位置输入：A

本行之`后`新增一行输入：o

本行之`前`新增一行输入：O（大写）

## VISUAL 模式

- 在`普通模式`下，按下 v 可以选择文本

### 撤销

- 在`普通模式`下，按 u 可以撤销上一次操作

### 删除（或剪切）

- 在`普通模式`下，剪切为 d，复制为 y，粘贴为 p

删除当前光标字符：x

剪切：cc

删除单词：ciw

删除当前单词：dw

删除（或剪切）当前行：dd

删除（或剪切）后 3 行：3dd

删除（或剪切）光标到行首：d^

删除（或剪切）光标到行尾：d$

### 复制

- 在`普通模式`下，按 y 复制

复制当前字符：y

复制当前行：yy

复制后 3 行：3yy

复制光标到行首：y^

复制光标到行尾：y$

复制当前单词：yiw

### 粘贴

- 在`普通模式`下，按 p 粘贴

粘贴到光标之前：P（大写）

粘贴到光标之后：p（小写）

### 跳转

- 在`普通模式`下，按 g 跳转

跳转到文首：gg

跳转到文尾：G

跳转到第 8 行:8gg

跳转到第 8 行:8G

### 移动

- 在`普通模式`下

左：h

右：l

下：j

上：k

移动到下一个单词：w

移动到上一个单词：b

移动到行首：0（数字）

移动到行尾：$

### 翻页

翻页上一页：Ctrl+f

翻页上一页：Ctrl+u

## 底线模式

- 在`普通模式`下，按下`:`（冒号）或者`/`（斜杠）进入底线模式

### 退出

1、强制执行

```sh
:!
```

2、退出

```sh
:q
```

3、强制退出（不会保存）

```sh
:q! 或者 ZQ
```

### 保存

1、保存

```sh
:w
```

2、保存退出

```sh
:wq（:x）或者 ZZ
```

3、所有保存退出

```sh
:wqa（:xa）
```

### 文件重命名

```sh
:w 新的文件名
```

### 显示（取消）行号

1、显示行号

```sh
:set nu
```

2、取消行号

```sh
:set nonu
```

### 搜索

1、向后搜索

```sh
/关键词
```

2、向前搜索

```sh
?关键词
```

3、定位到第 n 行

```sh
:n
```

查找上一处：N

查找下一处：n

### 替换

1、当前行第一个替换

```sh
:s/要替换的内容/替换后的内容/
```

2、当前行全部替换

```sh
:s/要替换的内容/替换后的内容/g
```

3、全文替换

```sh
:%s/要替换的内容/替换后的内容/g
```

## 对应单词

增加文本
a/A(append)
i/I(insert)
o/O(open a line)

撤销
u(undo)

删除
d(delete)
dw(delet word)
dd(删除一行)
3dd(删除三行)
diw(delete inner word)
daw(delete around word)

x(删除一个字符)

修改
c(change)
ciw(change inner word)
ct)修改到右括号

使用 f 查找当前行
使用;查找下一个

基于单词
w(word)
b(back word)

ctrl+o 返回到之前位置

翻页:
ctrl+f(forward)
ctrl+u(upward)

y(yank)
p(paste)

## vim -h

```sh
用法: vim [参数] [文件 ..]       编辑指定的文件
  或: vim [参数] -               从标准输入(stdin)读取文本
  或: vim [参数] -t tag          编辑 tag 定义处的文件
  或: vim [参数] -q [errorfile]  编辑第一个出错处的文件

参数:
   --                   在这以后只有文件名
   -v                   Vi 模式 (同 "vi")
   -e                   Ex 模式 (同 "ex")
   -E                   Improved Ex mode
   -s                   安静(批处理)模式 (只能与 "ex" 一起使用)
   -d                   Diff 模式 (同 "vimdiff")
   -y                   容易模式 (同 "evim"，无模式)
   -R                   只读模式 (同 "view")
   -Z                   限制模式 (同 "rvim")
   -m                   不可修改(写入文件)
   -M                   文本不可修改
   -b                   二进制模式
   -l                   Lisp 模式
   -C                   兼容传统的 Vi: 'compatible'
   -N                   不完全兼容传统的 Vi: 'nocompatible'
   -V[N][fname]         Be verbose [level N] [log messages to fname]
   -D                   调试模式
   -n                   不使用交换文件，只使用内存
   -r                   列出交换文件并退出
   -r (跟文件名)                恢复崩溃的会话
   -L                   同 -r
   -A                   以 Arabic 模式启动
   -H                   以 Hebrew 模式启动
   -T <terminal>        设定终端类型为 <terminal>
   --not-a-term         Skip warning for input/output not being a terminal
   --ttyfail            Exit if input or output is not a terminal
   -u <vimrc>           使用 <vimrc> 替代任何 .vimrc
   --noplugin           不加载 plugin 脚本
   -p[N]                打开 N 个标签页 (默认值: 每个文件一个)
   -o[N]                打开 N 个窗口 (默认值: 每个文件一个)
   -O[N]                同 -o 但垂直分割
   +                    启动后跳到文件末尾
   +<lnum>              启动后跳到第 <lnum> 行
   --cmd <command>      加载任何 vimrc 文件前执行 <command>
   -c <command>         加载第一个文件后执行 <command>
   -S <session>         加载第一个文件后执行文件 <session>
   -s <scriptin>        从文件 <scriptin> 读入正常模式的命令
   -w <scriptout>       将所有输入的命令追加到文件 <scriptout>
   -W <scriptout>       将所有输入的命令写入到文件 <scriptout>
   -x                   编辑加密的文件
   --startuptime <file> Write startup timing messages to <file>
   --log <file> Start logging to <file> early
   -i <viminfo>         使用 <viminfo> 取代 .viminfo
   --clean              'nocompatible', Vim defaults, no plugins, no viminfo
   -h  或  --help       打印帮助(本信息)并退出
   --version            打印版本信息并退出
```

## 常见错误

### E505

```sh
E505: "vimrc" is read-only (add ! to override)
```

- 无法保存退出，执行强制退出也不行:wq!

```sh
"vimrc" E212: Can't open file for writing
Press ENTER or type command to continue
```

- 解决方法：sudo vim 运行
