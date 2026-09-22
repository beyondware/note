# 前期准备

## 下载 qemu-img

> https://cloudbase.it/qemu-img-windows/

加入到系统变量环境，后续 .dmg 转换为 .vmdk

## 下载 OC4VM

> https://github.com/DrDonk/OC4VM

```sh
oc4vm\tools\windows\recoveryOS.exe
```

下载一个 sequoia.dmg，转换成 sequoia.vmdk

## 拖入虚拟机，根据实际情况进行调整

```sh
oc4vm\vmware\intel\macos.vmx
```

## 导入 sequoia.vmdk

编辑虚拟机设置——添加——硬盘——SATA（推荐）——使用现有虚拟磁盘——sequoia.vmdk

## 设置开机顺序

硬盘 500G——点（高级）——设置为0:5（占用0:0，新硬盘无法设置）

新硬盘——点（高级）——设置为0:0

CD/DVD——点（高级）——设置为0:1

硬盘 500G——点（高级）——设置为0:2（将0:5改为0:2）

# 启动虚拟机进行安装

由于下载的是基础包，安装过程用时可能会很久。

# 优化

系统设置——通用——登录项与扩展——共享和访达，关闭：所有复选项

系统设置——辅助功能——显示，打开：减弱动态效果和降低透明度

系统设置——桌面与程序坞——最小化窗口时使用，神奇效果改为缩放效果；关闭：弹跳打开应用程序

系统设置——隐私与安全性——辅助功能，打开：vmware-tools-daemon

# 参考

> https://sspai.com/post/106062

# macOS 升级

## 查看可升级的版本

```sh
softwareupdate --list-full-installers
```

## 指定升级到的版本

```sh
softwareupdate --fetch-full-installer --full-installer-version <版本号>
```
