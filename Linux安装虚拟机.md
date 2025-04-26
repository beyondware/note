# Arch

1、是否虚拟化

```sh
LC_ALL=C lscpu | grep Virtualization
```

输出结果

> Virtualization:     VT-x

2、安装

```sh
sudo pacman -S qemu-full libvirt virt-manager virt-install virt-viewer bridge-utils dnsmasq openbsd-netcat
```

```sh
qemu-full 或者 qemu-base：通用硬件模拟器和虚拟机管理器
libvirt：管理虚拟化平台工具
virt-manager：图形化的虚拟机管理工具
virt-install：命令行工具，用于创建虚拟机
virt-viewer：轻量级的远程查看工具
bridge-utils：提供桥接网络的管理工具
dnsmasq：为虚拟机提供 NAT 网络连接
openbsd-netcat：用于网络调试和数据传输的工具，支持 TCP 和 UDP 协议
```

3、选装

```sh
sudo pacman -S swtpm vde2 ebtables spice-vdagent qemu-guest-agent
```

```sh
swtpm：允许虚拟机使用 TPM 功能而不需要物理硬件支持，例如：安装 Windows 11
vde2：高级虚拟网络配置
ebtables：用户空间工具，用于管理 Linux 内核的网桥过滤表
spice-vdagent：提供剪贴板共享、文件拖放等功能
qemu-guest-agent：提供虚拟机与宿主机之间的管理和通信能力
```

4、启动 libvirtd 服务

```sh
sudo systemctl start libvirtd
或者
sudo service libvirtd start
```

5、开机自启动 libvirtd 服务

```sh
sudo systemctl enable --now libvirtd
```

6、编辑

```sh
sudo vim /etc/libvirt/libvirtd.conf
```

取消注释#

```sh
unix_sock_group = 'libvirt'
unix_sock_rw_perms = '0770'
```

7、将用户名添加到 libvirt 组

```sh
sudo usermod $USER -aG libvirt,kvm
```

8、验证 libvirt

```sh
virsh version
```

输出结果

```sh
Compiled against library: libvirt 10.0.0
Using library: libvirt 10.0.0
Using API: QEMU 10.0.0
Running hypervisor: QEMU 8.2.2
```

9、运行

```sh
virt-manager
```

10、启动虚拟网络

```sh
pacman -Ql libvirt | grep networks
```

```sh
sudo virsh net-define /etc/libvirt/qemu/networks/default.xml
```

输出结果

> 从 default定义网络/etc/libvirt/qemu/networks/default.xml

11、开机自启动

```sh
sudo virsh net-autostart default
```

# Fedora

1、是否虚拟化

```sh
LC_ALL=C lscpu | grep Virtualization
```

输出结果

> Virtualization:     VT-x

2、安装

```sh
sudo dnf install qemu-kvm virt-manager libvirt virt-viewer virt-install
```

3、启动 libvirtd 服务

```sh
sudo systemctl start libvirtd
```

4、开机自启动 libvirtd 服务

```sh
sudo systemctl enable --now libvirtd
```

5、编辑

```sh
sudo vim /etc/libvirt/libvirtd.conf
```

取消注释#

```sh
unix_sock_group = 'libvirt'
unix_sock_rw_perms = '0770'
```

6、将用户名添加到 libvirt 组

```sh
sudo usermod -aG libvirt $USER
sudo usermod -aG kvm $USER
```

是否添加到组

```sh
id $USER
```

7、验证 libvirt

```sh
virsh version
```

输出结果

```sh
Compiled against library: libvirt 10.0.0
Using library: libvirt 10.0.0
Using API: QEMU 10.0.0
Running hypervisor: QEMU 8.2.2
```

8、运行

```sh
virt-manager
```

9、宿主机和虚拟机之间共享粘贴板

```sh
sudo dnf install spice-vdagent
```

```sh
sudo systemctl start spice-vdagent
sudo systemctl enable --now spice-vdagent
```

# Ubuntu

1、是否虚拟化

```sh
LC_ALL=C lscpu | grep Virtualization
```

输出结果

> Virtualization:     VT-x

2、安装

```sh
sudo apt install virt-manager qemu-system qemu-utils libvirt-daemon-system libvirt-clients bridge-utils 
```

3、启动 libvirtd 服务

```sh
sudo systemctl start libvirtd
```

4、开机自启动 libvirtd 服务

```sh
sudo systemctl enable --now libvirtd
```

5、编辑

```sh
sudo vim /etc/libvirt/libvirtd.conf
```

取消注释#

```sh
unix_sock_group = 'libvirt'
unix_sock_rw_perms = '0770'
```

6、将用户名添加到 libvirt 组

```sh
sudo usermod -aG libvirt $USER
sudo usermod -aG kvm $USER
```

是否添加到组

```sh
id $USER
```

7、检查 KVM

```sh
lsmod | grep -i kvm
```

8、运行

```sh
virt-manager
```

# 报错

## 报错1

```sh
Unable to connect to libvirt qemu:///system
Verify that the 'libvirtd' daemon is running.
请验证 'libvirtd' 守护进程是否正在运行。
```

1、启动 libvirtd 服务

```sh
sudo systemctl start libvirtd
```

2、启动 libvirtd 服务后，仍报错，需提权

```sh
sudo chmod 777  /var/run/libvirt/libvirt-sock
```

## 报错2

```sh
WARNING : KVM 不可用。这可能是因为没有安装 KVM 软件包，或者没有载入 KVM 内核模块。您的虚拟机可能性很差。
```

解决方法：开启虚拟化

## 报错3

```sh
Error starting domain: Requested operation is not valid: network 'default' is not active
启动域时出错: 所需操作无效：网络 ‘default’ 未激活
```

1、确实是否处于非活动状态

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

Overview（概述）

Chipset=Q35

Firmware=BIOS

Add hardware（添加硬件）→添加 TPM

Model=TIS

Backend=Emulated device

Version=2.0
