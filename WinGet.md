# 下载准备

1、Microsoft.DesktopAppInstaller.msixbundle 和 License1.xml

> https://github.com/microsoft/winget-cli

2、VCLibs

```sh
Microsoft.VCLibs.appx
```

3、Microsoft.UI.Xaml

```sh
Microsoft.UI.Xaml.appx
```

# 安装过程

1、以管理员身份运行 PowerShell

2、VCLibs

```sh
Add-AppxPackage -Path <Microsoft.VCLibs..appx>
```

3、Microsoft.UI.Xaml

```sh
Add-AppxPackage -Path <Microsoft.UI.Xaml.appx>
```

警告：未安装 VCLibs 和 Microsoft.UI.Xaml 依赖项，WinGet 安装程序将失败（没有任何错误/警告消息）。
具体而言，“winget.exe”文件未添加到“C：\Users\用户名\AppData\Local\Microsoft\WindowsApps”

4、WinGet

```sh
Add-AppxPackage -Path <Microsoft.DesktopAppInstaller.msixbundle>
```

5、配置许可证

```sh
Add-AppxProvisionedPackage -Online -PackagePath <Microsoft.DesktopAppInstaller.msixbundle> -LicensePath <License1.xml>
```

# 报错信息

Add-AppxPackage : Deployment failed with HRESULT: 0x80073CF3, 包无法进行更新、相关性或冲突验证。
Windows 无法安装程序包Microsoft.DesktopAppInstaller_1.29.280.0_x64__8wekyb3d8bbwe，因为此程序包依赖于找不到的框架。提供
由"CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US"发布的框架"Microsoft.WindowsAppRunt
ime.1.8"，其中包含中性或x64处理器体系结构和最低版本8000.616.304.0，以及要安装的此包。

下载 1.8 版本

> https://learn.microsoft.com/zh-cn/windows/apps/windows-app-sdk/downloads-archive

确认安装版本

```sh
Get-AppxPackage *Microsoft.WindowsAppRuntime*
```

Add-AppxPackage : Deployment failed with HRESULT: 0x80073CF3, 包无法进行更新、相关性或冲突验证。
Windows 无法安装程序包Microsoft.DesktopAppInstaller_1.29.280.0_x64__8wekyb3d8bbwe，因为此程序包依赖于找不到的框架。提供
由"CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US"发布的框架"Microsoft.VCLibs.140.00"
，其中包含中性或x64处理器体系结构和最低版本14.0.33519.0，以及要安装的此包。

确认安装版本

```sh
Get-AppxPackage *Microsoft.VCLibs*
```

# 参考

> https://learn.microsoft.com/zh-cn/windows/iot/iot-enterprise/deployment/install-winget-windows-iot

由于文档未更新相关软件链接，导致安装失败，获取最新下载地址

> https://store.rg-adguard.net/

> https://apps.microsoft.com/detail/9wzdncrfjbmp

