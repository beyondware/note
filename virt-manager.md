## 安装 virt-manager

```sh
sudo apt install virt-manager
```

## 存储目录

```sh
/var/lib/libvirt/images
```

1、当前用户添加到 libvirt 组

```sh
sudo adduser $USER libvirt
```

确认是否添加到组

```sh
id $USER
```

2、无法连接到 libvirt

```sh
Unable to connect to libvirt qemu:///system
Verify that the 'libvirtd' daemon is running.
```

启动 libvirt 守护程序

```sh
sudo systemctl start libvirtd
```

3、启动域时出错

```sh
Error starting domain: Requested operation is not valid: network 'default' is not active
```

启动虚拟网络

```sh
sudo virsh net-start default
```

## 分辨率

Video Virtio > Model - Virtio

View > Scale Display > Always

## virt-manager 设置 TPM 2.0

```sh
sudo apt install ovmf swtpm swtpm-tools
```

## 安装 Windows 11

> Memory：8GB

> CPUs：4（最小值）

> 存储容量：60GB

Overview：

> Chipset=Q35

> Firmware=BIOS

Add Hardware（添加硬件） > TPM

> Type: Emulated

> Model: TIS

> Version: 2.0

