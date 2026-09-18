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


```

