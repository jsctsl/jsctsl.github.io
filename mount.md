## 挂载磁盘到目录

### 检查未挂载磁盘

```shell
lsblk
```

```
NAME   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINTS
vda    254:0    0   40G  0 disk 
├─vda1 254:1    0    1M  0 part 
├─vda2 254:2    0  191M  0 part /boot/efi
└─vda3 254:3    0 39.8G  0 part /
vdb    254:16   0   60G  0 disk 
└─vdb1 254:17   0   60G  0 part 

# vdb1 未挂载
```

### 挂载磁盘到目录

```shell
mkdir /mnt/data

mount /dev/vdb1 /mnt/data
```

## 取消挂载

```
umount /mnt/data
# 或
umount /dev/vdb1
```

