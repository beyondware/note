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
sudo systemctl start libvirtd 或者 sudo service libvirtd start
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

unix_sock_group = 'libvirt'
unix_sock_rw_perms = '0770'

6、将用户名添加到 libvirt 组

```sh
sudo usermod -aG libvirt $USER
sudo usermod -aG kvm $USER
```

是否添加到组

```sh
id $USER
```

7、验证 libvirt 是否正常启动

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

# Ubuntu

1、是否虚拟化

```sh
LC_ALL=C lscpu | grep Virtualization
```

输出结果

> Virtualization:     VT-x

2、安装

```sh
sudo apt install virt-manager qemu-system qemu-utils libvirt-daemon-system
```

3、启动 libvirtd 服务

```sh
sudo systemctl start libvirtd 或者 sudo service libvirtd start
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

unix_sock_group = 'libvirt'
unix_sock_rw_perms = '0770'

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

# 宿主机和虚拟机之间共享粘贴板

```sh
sudo dnf install spice-vdagent
```

```sh
sudo systemctl start spice-vdagent
sudo systemctl enable --now spice-vdagent
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
Error starting domain: Requested operation is not valid: network 'default' is not active
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


