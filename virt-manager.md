## 安装 virt-manager

```sh
sudo apt install virt-manager
```

存储目录
/var/lib/libvirt/images

1、当前用户添加到 libvirt 组
sudo adduser $USER libvirt

确认是否添加到组

id $USER

2、无法连接到 libvirt

```sh
Unable to connect to libvirt qemu:///system
Verify that the 'libvirtd' daemon is running.
```

启动 libvirt 守护程序

sudo systemctl start libvirtd


3、启动域时出错

```sh
Error starting domain: Requested operation is not valid: network 'default' is not active
```

启动虚拟网络
sudo virsh net-start default

4、匹配分辨率

Video Virtio > Model 选择：Virtio

View > Scale Display > Always

5、virt-manager 设置 TPM 2.0

sudo apt install ovmf swtpm swtpm-tools


6、安装 Windows 11

Memory：8GB

CPUs：4（最小值）

存储容量：60GB

Overview：

Chipset=Q35

Firmware=BIOS

Add Hardware（添加硬件） > TPM

Type: Emulated
Model: TIS
Version: 2.0

