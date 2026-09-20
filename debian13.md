### 配置网络

```shell
root@debian:~# cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
allow-hotplug ens33
iface ens33 inet static
	address 192.168.200.181/24
	gateway 192.168.200.254
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 221.131.143.69 112.4.0.55
	dns-search debian.local

```



### 系统运行方式

```
# 查看
systemctl get-default

# 桌面
systemctl set-default graphical.target

# 命令行
systemctl set-default multi-user.target
```

### 区域语言

```shell
locale
LANG=C
LANGUAGE=C
LC_CTYPE="C"
LC_NUMERIC="C"
LC_TIME="C"
LC_COLLATE="C"
LC_MONETARY="C"
LC_MESSAGES="C"
LC_PAPER="C"
LC_NAME="C"
LC_ADDRESS="C"
LC_TELEPHONE="C"
LC_MEASUREMENT="C"
LC_IDENTIFICATION="C"
LC_ALL=


cat /etc/locale.conf 
LANG=en_US.UTF-8
LANGUAGE=en_US:en


sudo localectl list-locales
C.UTF-8
en_US.UTF-8
zh_CN.UTF-8


sudo localectl set-locale LANG=en_US.UTF-8

sudo localectl status
# 结果
System Locale: LANG=en_US.UTF-8
    VC Keymap: (unset)         
   X11 Layout: us
    X11 Model: pc105

```

### 时区配置

```shell
# 查询
sudo timedatectl show
# 结果
Timezone=Asia/Shanghai
LocalRTC=no
CanNTP=yes
NTP=yes
NTPSynchronized=yes
TimeUSec=Sat 2026-09-19 14:56:09 SST
RTCTimeUSec=Sat 2026-09-19 14:56:09 SST

# 查询
sudo timedatectl list-timezones | grep UTC
# 结果
Etc/UTC
UTC

# 设置时区
sudo timedatectl set-timezone Etc/UTC

# 验证
sudo timedatectl show
# 结果
Timezone=Etc/UTC
LocalRTC=no
CanNTP=yes
NTP=yes
NTPSynchronized=yes
TimeUSec=Sun 2026-09-20 01:59:00 UTC
RTCTimeUSec=Sun 2026-09-20 01:59:00 UTC
```

### 新盘挂载

```shell
# 磁盘检查
sudo lsblk -f
## 输出结果
NAME   FSTYPE FSVER LABEL UUID                                 FSAVAIL FSUSE% MOUNTPOINTS
sda                                                                           
├─sda1 ext4   1.0         820c4b10-2f0b-4f5e-bb77-f73c9b69312b    6.4G    12% /
├─sda2                                                                        
├─sda5 ext4   1.0         2d9ee523-5477-4bef-adf6-9c120e4555ca    1.9G    13% /var
├─sda6 swap   1           f968ce51-6dbb-4f9a-a911-fb547db5f1e8                [SWAP]
├─sda7 ext4   1.0         828f04d4-8a38-45b2-b2ef-ed7700621e01  701.7M     0% /tmp
└─sda8 ext4   1.0         c4cf5b24-667e-4874-8a9c-60984a063a9c   24.8G     0% /home
sdb                                                                           
### sdb 为新硬盘

# 检查工具是否安装
sudo parted -v
## 输出结果
-bash: parted: command not found

# 工具安装
sudo apt install --no-install-recommends -y parted
## 输出结果
Installing:                     
  parted

Installing dependencies:
  libparted2t64

Suggested packages:
  libparted-dev  libparted-i18n  parted-doc

Summary:
  Upgrading: 0, Installing: 2, Removing: 0, Not Upgrading: 0
  Download size: 340 kB
  Space needed: 683 kB / 6,916 MB available

Get:1 http://deb.debian.org/debian trixie/main amd64 libparted2t64 amd64 3.6-5 [300 kB]
Get:2 http://deb.debian.org/debian trixie/main amd64 parted amd64 3.6-5 [40.2 kB]
Fetched 340 kB in 1s (360 kB/s)   
Selecting previously unselected package libparted2t64:amd64.
(Reading database ... 39659 files and directories currently installed.)
Preparing to unpack .../libparted2t64_3.6-5_amd64.deb ...
Adding 'diversion of /lib/x86_64-linux-gnu/libparted.so.2 to /lib/x86_64-linux-gnu/libparted.so.2.usr-is-merged by libparted2t64'
Adding 'diversion of /lib/x86_64-linux-gnu/libparted.so.2.0.5 to /lib/x86_64-linux-gnu/libparted.so.2.0.5.usr-is-merged by libparted2t64'
Unpacking libparted2t64:amd64 (3.6-5) ...
Selecting previously unselected package parted.
Preparing to unpack .../parted_3.6-5_amd64.deb ...
Unpacking parted (3.6-5) ...
Setting up libparted2t64:amd64 (3.6-5) ...
Removing 'diversion of /lib/x86_64-linux-gnu/libparted.so.2 to /lib/x86_64-linux-gnu/libparted.so.2.usr-is-merged by libparted2t64'
Removing 'diversion of /lib/x86_64-linux-gnu/libparted.so.2.0.5 to /lib/x86_64-linux-gnu/libparted.so.2.0.5.usr-is-merged by libparted2t64'
Setting up parted (3.6-5) ...
Processing triggers for libc-bin (2.41-12+deb13u4) ...
Processing triggers for man-db (2.13.1-1) ...


# 检查工具安装结果
sudo parted -v
## 输出结果
parted (GNU parted) 3.6
Copyright (C) 2023 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <https://gnu.org/licenses/gpl.html>.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Written by <http://git.debian.org/?p=parted/parted.git;a=blob_plain;f=AUTHORS>.

# 创建分区
## sudo parted /dev/<设备名称> --script mklabel gpt mkpart <自定义分区名称> <分区起始容量> <分区终止容量>
## 将设备名称为sdb的云盘容量全部划分给单个分区
sudo parted /dev/sdb --script mklabel gpt mkpart primary 1MiB 100%
## 将设备名称为sdc的云盘容量划分给两个分区，第一个名为primary分区20G，剩余容量全都划分给第二个名为secondary的分区
sudo parted /dev/sdc --script mklabel gpt mkpart primary 1MiB 50GiB mkpart secondary 50GiB 100%


# 检查是否对齐
## 查看分区编号
parted /dev/sdb print
### 输出结果
Model: VMware Virtual disk (scsi)
Disk /dev/sdb: 64.4GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name     Flags
 1      1049kB  64.4GB  64.4GB               primary


## 检查是否对齐
sudo parted /dev/sdb align-check optimal 1
### 输出结果
1 aligned

# 刷新磁盘分区表
sudo partprobe

# 查看分区创建是否成功
sudo lsblk
## 输出结果
NAME   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINTS
sda      8:0    0   40G  0 disk 
├─sda1   8:1    0    8G  0 part /
├─sda2   8:2    0    1K  0 part 
├─sda5   8:5    0  2.5G  0 part /var
├─sda6   8:6    0    2G  0 part [SWAP]
├─sda7   8:7    0  787M  0 part /tmp
└─sda8   8:8    0 26.7G  0 part /home
sdb      8:16   0   60G  0 disk 
└─sdb1   8:17   0   60G  0 part 

# 创建文件系统
sudo mkfs -t ext4 /dev/sdb1
## 输出结果
mke2fs 1.47.2 (1-Jan-2025)
Creating filesystem with 15728128 4k blocks and 3932160 inodes
Filesystem UUID: 93132397-ca88-475c-a536-979c1c32e6f7
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424

Allocating group tables: done                            
Writing inode tables: done                            
Creating journal (65536 blocks): done
Writing superblocks and filesystem accounting information: done   


# 检查文件系统是否创建成功
sudo lsblk -f
## 输出结果
NAME   FSTYPE FSVER LABEL UUID                                 FSAVAIL FSUSE% MOUNTPOINTS
sda                                                                           
├─sda1 ext4   1.0         820c4b10-2f0b-4f5e-bb77-f73c9b69312b    6.4G    12% /
├─sda2                                                                        
├─sda5 ext4   1.0         2d9ee523-5477-4bef-adf6-9c120e4555ca    1.9G    13% /var
├─sda6 swap   1           f968ce51-6dbb-4f9a-a911-fb547db5f1e8                [SWAP]
├─sda7 ext4   1.0         828f04d4-8a38-45b2-b2ef-ed7700621e01  701.7M     0% /tmp
└─sda8 ext4   1.0         c4cf5b24-667e-4874-8a9c-60984a063a9c   24.8G     0% /home
sdb                                                                           
└─sdb1 ext4   1.0         93132397-ca88-475c-a536-979c1c32e6f7
### sdb1 ext4 表示成功

# 临时挂载文件系统
sudo mkdir /data && sudo mount /dev/sdb1 /data
# 删除挂载文件系统
sudo umount /dev/sdb1


# 开机挂载文件系统
sudo nano /etc/fstab
## 追加行
UUID=93132397-ca88-475c-a536-979c1c32e6f7 /data ext4 defaults 0 0

# 重载服务
sudo systemctl daemon-reload
# 重新挂载
sudo mount -a


```

