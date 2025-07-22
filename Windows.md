# 跳过联网注册 Windows 11 账户

按<kbd>Shift</kbd> + <kbd>F10</kbd>组合键打开命令提示符，输入以下命令：

```sh
start ms-cxh:localonly
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
