# 获取 Shizuku 权限

查看连接设备

```sh
adb devices
```

停用多余设备

```sh
adb kill-server
```

出现“是否允许调试”的对话框，勾选“总是允许”后确认

```sh
adb devices
adb tcpip 5555
```

在手机设备 Shizuku 指令

# 当前用户卸载

查看 adb 版本

```sh
adb version
```

开启 adb

```sh
adb start-server
```

列出所有已安装应用的包名

```sh
adb shell pm list packages
```

卸载系统应用（仅当前用户）

```sh
adb shell pm uninstall -k --user 0 <包名>
```

输出 Success，表示卸载成功。

恢复

```sh
adb shell pm install-existing --user 0 <包名>
```

禁用

```sh
adb shell pm disable-user <包名>
```

启用

```sh
adb shell pm enable <包名>
```

卸载

```sh
adb uninstall <包名>
```

多个设备，需指定设备序列号，通过 adb devices 获取

```sh
adb -s <设备序列号> uninstall <包名>
```

# 彻底卸载系统应用

获取 Root 权限

```sh
adb root
```

```sh
adb remount
```

remount sucessed 代表成功

查找 APK 文件路径

```sh
adb shell pm path <包名>
```

删除 APK 文件

```sh
adb shell rm -rf <文件路径.apk>
```

重启设备

```sh
adb reboot
```

验证卸载结果

```sh
adb shell pm list packages | grep <包名>
```

获取当前正在使用的包名

```sh
adb shell "dumpsys window | grep mCurrentFocus" 
```
