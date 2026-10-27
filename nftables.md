### 检查是否安装

```shell
sudo systemctl list-unit-files | grep nftables

# 输出内容
nftables.service                                                          disabled        enabled

```

### 启用

```shell
systemctl enable nftables
# 输出内容
Created symlink '/etc/systemd/system/sysinit.target.wants/nftables.service' → '/usr/lib/systemd/system/nftables.service'.

```

