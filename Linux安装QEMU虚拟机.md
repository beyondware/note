# 是否虚拟化

```sh
LC_ALL=C lscpu | grep Virtualization
```

输出结果

> Virtualization:     VT-x

# Arch

## 安装

```sh
sudo pacman -S qemu-full qemu-emulators-full qemu-guest-agent libvirt virt-install virt-viewer virt-manager dnsmasq vde2 bridge-utils openbsd-netcat swtpm ebtables spice-vdagent 
```

```sh
qemu-full（包含 qemu-emulators-full、qemu-base、qemu-desktop）：通用硬件模拟器和虚拟机管理器
qemu-guest-agent：提供虚拟机与宿主机之间的管理和通信能力
libvirt：管理虚拟化平台工具
virt-install：命令行工具，用于创建虚拟机
virt-viewer：轻量级的远程查看工具
virt-manager：图形化的虚拟机管理工具
dnsmasq：为虚拟机提供 NAT 网络连接
vde2：一种虚拟交换机，可以将多个虚拟机（本地和远程）连接在一起
bridge-utils：提供桥接网络的管理工具
openbsd-netcat：用于网络调试和数据传输的工具，支持 TCP 和 UDP 协议
swtpm：允许虚拟机使用 TPM 功能而不需要物理硬件支持，例如：安装 Windows 11
ebtables：用户空间工具，用于管理 Linux 内核的网桥过滤表
spice-vdagent：提供剪贴板共享、文件拖放等功能
```

## 查看 virsh 的版本信息

```sh
virsh version
```

输出结果

```sh
根据库编译：libvirt 11.6.0
使用库：libvirt 11.6.0
使用的 API: QEMU 11.6.0
运行管理程序: QEMU 10.0.3
```

## libvirt

### 启动 libvirtd 服务

```sh
sudo systemctl start libvirtd
或者
sudo service libvirtd start
```

### 开机自启动 libvirtd 服务

```sh
sudo systemctl enable --now libvirtd
```

### 编辑

```sh
sudo vim /etc/libvirt/libvirtd.conf
```

取消注释#

```sh
unix_sock_group = 'libvirt'
unix_sock_rw_perms = '0770'
```

### 将用户名添加到 libvirt 和 kvm 组

```sh
sudo usermod $USER -aG libvirt,kvm
```

## virsh

### 启动虚拟网络

```sh
pacman -Ql libvirt | grep networks
```

```sh
sudo virsh net-define /etc/libvirt/qemu/networks/default.xml
```

输出结果

> 从 default定义网络/etc/libvirt/qemu/networks/default.xml

### 默认虚拟网络设置

```sh
sudo EDITOR=vim virsh net-edit default
```

### 重启 libvirtd 使网络配置生效

```sh
sudo systemctl restart libvirtd
```

### 启动默认虚拟网络

```sh
sudo virsh net-start default
```

### 默认虚拟网络开机自启动

```sh
sudo virsh net-autostart default
```

### 查看所有虚拟网络状态（包括 default 网络）

```sh
sudo virsh net-list --all
```

## 运行 virt-manager

```sh
virt-manager
```

# Fedora

## 安装

```sh
sudo dnf install qemu-kvm virt-manager libvirt virt-viewer virt-install swtpm swtpm-tools
```

## 查看 virsh 的版本信息

```sh
virsh version
```

## libvirt

### 启动 libvirtd 服务

```sh
sudo systemctl start libvirtd
```

### 开机自启动 libvirtd 服务

```sh
sudo systemctl enable --now libvirtd
```

### 编辑

```sh
sudo vim /etc/libvirt/libvirtd.conf
```

取消注释#

```sh
unix_sock_group = 'libvirt'
unix_sock_rw_perms = '0770'
```

### 将用户名添加到 libvirt 和 kvm 组

```sh
sudo usermod -aG libvirt $USER
sudo usermod -aG kvm $USER
```

是否添加到组

```sh
id $USER
```

## 运行 virt-manager

```sh
virt-manager
```

## 宿主机和虚拟机之间共享粘贴板

### 安装 spice-vdagent

```sh
sudo dnf install spice-vdagent
```

### 启动

```sh
sudo systemctl start spice-vdagent
```

### 开机自启动

```sh
sudo systemctl enable --now spice-vdagent
```

# Ubuntu

## 安装

```sh
sudo apt install qemu-system qemu-utils libvirt-daemon-system libvirt-clients virt-manager bridge-utils swtpm swtpm-tools 
```

## 检查内核模块

```sh
lsmod | grep kvm
```

## libvirt

### 启动 libvirtd 服务

```sh
sudo systemctl start libvirtd
```

### 开机自启动 libvirtd 服务

```sh
sudo systemctl enable --now libvirtd
```

### 编辑

```sh
sudo vim /etc/libvirt/libvirtd.conf
```

取消注释#

```sh
unix_sock_group = 'libvirt'
unix_sock_rw_perms = '0770'
```

### 将用户名添加到 libvirt 和 kvm 组

```sh
sudo usermod -aG libvirt $USER
sudo usermod -aG kvm $USER
```

是否添加到组

```sh
id $USER
```

## 运行 virt-manager

```sh
virt-manager
```

# 报错

## libvirtd 守护进程未运行

```sh
Unable to connect to libvirt qemu:///system
Verify that the 'libvirtd' daemon is running.  ##请验证 'libvirtd' 守护进程是否正在运行。
```

1、查看 libvirtd 当前状态

```sh
sudo systemctl status libvirtd
```

2、如果未运行，启动 libvirtd 服务

```sh
sudo systemctl start libvirtd
```

3、开机自启动

```sh
sudo systemctl enable --now libvirtd
```

4、启动 libvirtd 服务后，仍报错，需提权

```sh
sudo chmod 777  /var/run/libvirt/libvirt-sock
```

## 系统虚拟化未开启

> WARNING : KVM 不可用。这可能是因为没有安装 KVM 软件包，或者没有载入 KVM 内核模块。您的虚拟机可能性很差。

是否虚拟化

```sh
LC_ALL=C lscpu | grep Virtualization
```

输出结果

> Virtualization:     VT-x

## 网络未激活

> Error starting domain: Requested operation is not valid: network 'default' is not active   ##启动域时出错: 所需操作无效：网络 ‘default’ 未激活

1、是否处于非活动状态

```sh
sudo virsh net-list --all
```

2、KVM 网络未激活，使用 virsh 启动网络

```sh
sudo virsh net-start --network default
```

```sh
sudo virsh net-autostart default
```

## 未连接到 hypervisor

> error: failed to connect to the hypervisor  ##错误：未连接到 hypervisor

1、查看 libvirtd 当前状态

```sh
sudo systemctl status libvirtd
```

2、如果未运行，启动 libvirtd 服务

```sh
sudo systemctl start libvirtd
```

3、开机自启动

```sh
sudo systemctl enable --now libvirtd
```

# 分辨率

Video Virtio > Model - Virtio

View > Scale Display > Always

# 安装 Windows 11

1、设置条件

Memory（内存）：8GB

CPUs：4（最小值）

存储容量：60GB

2、创建步骤

创建第2步

勾选：Automatically detect operating system based on install media（自动检测操作系统类型和版本）

创建第4步

勾选：Select or Create custom storage（选择或创建自定义存储）

创建第5步

勾选：Customize configuration before install（安装前自定义配置）

3、Overview（概述）

Chipset=Q35

Firmware=BIOS

Add hardware（添加硬件）→添加 TPM

Model=TIS

Backend=Emulated device

Version=2.0

显示协议 Spice

Spice 服务器→类型=Spice 服务器

添加硬件→通道（2个）

通道：名称选择 com.redhat.spice.0

通道：名称选择 org.qemu.guest_agent.0

显示虚拟硬件详细信息 -> 添加硬件 -> 存储 ，然后添加 VirtIO 驱动程序 ISO 文件

Show virtual hardware details -> Add Hardware -> Storage

> https://fedorapeople.org/groups/virt/virtio-win/direct-downloads/stable-virtio/virtio-win.iso
