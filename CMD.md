### 基础

```sh
不区分`大小写`
help：帮助
命令 /？：查询命令手册
Ctrl+C：强制中止
按 Tab 键：自动补全
历史命令：上/下方向键
exit：退出
```

### cls 清屏

cls:（CLear Screen）清屏

### Administrator

1、开启

```sh
net user administrator /active:yes
```

2、关闭

```sh
net user administrator /active:no
```

### 管理员已阻止你运行此应用

```sh
sfc /scannow
```

```s
gpedit.msc
```

### shutdown 关机、重启

1、关机

```sh
shutdown -s
```

2、重启

```sh
shutdown -r
```

3、注销

```sh
shutdown -l 或者 logoff
```

### cd 目录

cd:（change directory）切换目录

1、当前目录

```sh
cd.
```

2、切换上一级目录

```sh
cd..
```

3、切换根目录

```sh
cd \
```

### 切换盘符

```sh
e:  (如：E 盘)
```

### dir 目录

dir:（directory）目录

```sh
mkdir 或者 md：（make directory）创建目录
```

```sh
rmdir 或者 rd：（remove directory）删除目录
```

### del 删除

```sh
del：删除文件
```

### copy 复制

```sh
copy：复制文件
```

```sh
xcopy：复制目录
```

### move 移动

### rename 重命名

```sh
rename 或者 ren：重命名文件
```

### echo 输出

```sh
echo abc > a.txt
```

abc 内容`输入`到 a.txt

```sh
echo abc >> a.txt
```

abc 内容`追加`到 a.txt

### tasklist 进程

1、显示正在运行进程

```sh
tasklist
```

2、结束进程

```sh
taskkill /pid 进程编号
```

3、关闭程序

```sh
taskkill /im 程序名
```

4、运行程序

```sh
start 程序名
```

### ipconfig 网络

1、显示 IP 地址信息

```sh
ipconfig
```

2、清除本地 DNS 缓存

```sh
ipconfig /flushdns
```

3、延迟和丢包率

```sh
ping 61.139.2.69 -t
```

- 向（61.139.2.69）发包

- -t：连续发送
