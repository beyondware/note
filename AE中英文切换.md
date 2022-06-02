---
title: AE 中英文切换
author: beyondware
tags:
  - [cmd]
categories:
  - [Windows]
---

- AE 路径

```sh
D:\Adobe\Adobe After Effects 2021\Support Files\AMT
```

> 复制 2 份 application.xml 分别命名为 application_cn.xml 和 application_en.xml

- 打开 application_en.xml 文件，找到

```sh
key="installedLanguages">zh_CN
```

改成

```sh
key="installedLanguages">en_US
```

将下面代码，保存为.bat 运行，选择即可

- 注意：将 `ae_path=路径` 改成自己 AE 安装的路径

```sh
@echo off
echo - Produced by OrangePeel -
echo.

# 路径改为自己安装的位置

set ae_path="D:\Adobe\Adobe After Effects 2021\Support Files\AMT"

set /p lan=1.en 2.cn:

goto %lan%

:1
copy %ae_path%\application_en.xml %ae_path%\application.xml /y
exit

:2
copy %ae_path%\application_cn.xml %ae_path%\application.xml /y
exit
```
