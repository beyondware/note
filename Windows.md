# 跳过联网注册 Windows 11 账户

按<kbd>Shift</kbd> + <kbd>F10</kbd>组合键打开命令提示符

## 方法一

```sh
start ms-cxh:localonly  #创建本地账户
```

## 方法二

```sh
reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\OOBE /v BypassNRO /t REG_DWORD /d 1 /f
```

```sh
shutdown /r /t 0
```

## 方法三

输入regedit，打开注册表编辑器

路径：

```sh
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\OOBE
```

新建一个DWORD（32位）值，命名为BypassNRO。键值修改为1，保存并重启。

```sh
net user "User Name" /add
net localgroup "Administrators" "User Name" /add
cd OOBE
msoobe && shutdown -r
```

# Windows 关闭端口扫描防护筛选器的日志写入功能（管理员权限执行）

```sh
netsh wfp set options netevents=off
```

# 右键菜单

## 经典右键菜单

```sh
reg.exe add "HKCU\Software\Classes\CLSID\{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}\InprocServer32" /f /ve
```

重启资源管理器

```sh
taskkill /f /im explorer.exe & start explorer.exe
```

## 还原右键菜单

```sh
reg.exe delete "HKCU\Software\Classes\CLSID\{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}\InprocServer32" /va /f
```

重启资源管理器

```sh
taskkill /f /im explorer.exe & start explorer.exe
```

# 删除桌面右键 UWTSettings

```sh
REG DELETE "HKEY_CLASSES_ROOT\DesktopBackground\Shell\UWTSettings" /f
```

# 暂停 Windows 更新

按 Win + X 键选择 Windows PowerShell (管理员)

```sh
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\WindowsUpdate\UX\Settings" /v FlightSettingsMaxPauseDays /t reg_dword /d 10000 /f
```

# 超级管理员（管理员权限运行）

## 启用超级管理员帐户

```sh
net user administrator /active:yes
```

## 禁用超级管理员帐户

```sh
net user administrator /active:no
```

# can not create temp folder archeve

右击“我的电脑”选择“属性”－“高级”，单击“环境变量”按钮，然后单击里边的“新建”按钮，在变量名中输入“TEMP”，值设为“%USERPROFILE%\AppData\Local\Temp”
