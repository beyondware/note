### 基础

不区分`大小写`
help：帮助
命令 /？：查询命令手册
cls ：（CLear Screen）清屏
Ctrl+C：强制中止
按 Tab 键：自动补全
历史命令：上/下方向键
exit：退出

### 开关机

关机

> shutdown -s

重启

> shutdown -r

注销

> shutdown -l 或者 logoff

### 切换目录

- cd：（change directory）切换目录

当前目录

> cd.

切换上一级目录

> cd..

切换根目录

> cd \

切换盘符(如：E 盘)

> e:

目录

> dir：（directory）查看当前目录

> mkdir 或者 md：（make directory）创建目录

> rmdir 或者 rd：（remove directory）删除目录

删除

> del：删除文件

复制

> copy：复制文件

> xcopy：复制目录

移动

> move

重命名

> rename 或者 ren：重命名文件

### 输出

- echo

abc 内容`输入`到 a.txt

> echo abc > a.txt

abc 内容`追加`到 a.txt

> echo abc >> a.txt

### 进程

显示正在运行进程

> tasklist

结束进程

> taskkill /pid 进程编号

关闭程序

> taskkill /im 程序名

运行程序

> start 程序名

### 网络

显示 IP 地址信息

> ipconfig

清除本地 DNS 缓存

> ipconfig /flushdns

ping IP 地址：延迟和丢包率

> ping 61.139.2.69 -t

- 向（61.139.2.69）发包

- -t：连续发送
