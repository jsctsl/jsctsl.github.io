# 阿里云ECS服务器

## 挂载数据盘

### 查看设备UUID

```shell
sudo lsblk -f
NAME   FSTYPE FSVER LABEL UUID                                 FSAVAIL FSUSE% MOUNTPOINTS
vda                                                                           
├─vda1                                                                        
├─vda2 vfat   FAT32       AFE9-C30B                             179.3M     5% /boot/efi
└─vda3 ext4   1.0         b4a85243-0f2f-49c2-b618-45caef7ce79a     35G     6% /
vdb                                                                           
└─vdb1 ext4   1.0         a53e8d33-ed76-451e-9755-56491f8f4ce5
```

### 配置文件

```shell
sudo sh -c "echo `sudo blkid /dev/vdb1 | awk '{print \$2}' | sed 's/\"//g'` /data ext4 defaults 0 0 >> /etc/fstab"

# /etc/fstab 文件追加下行内容
# UUID=a53e8d33-ed76-451e-9755-56491f8f4ce5 /data ext4 defaults 0 0


blkid /dev/vdb1
/dev/vdb1: UUID="a53e8d33-ed76-451e-9755-56491f8f4ce5" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="8bf4a8f2-01"
blkid /dev/vdb1 | awk '{print $2}'
UUID="a53e8d33-ed76-451e-9755-56491f8f4ce5"
blkid /dev/vdb1 | awk '{print $2}' | sed 's/\"//g'
UUID=a53e8d33-ed76-451e-9755-56491f8f4ce5
```

### 格式

```
<file system> <mount point>   <type>  <options>       <dump>  <pass>
UUID=a53e8d33-ed76-451e-9755-56491f8f4ce5 /data ext4 defaults 0 0
```

