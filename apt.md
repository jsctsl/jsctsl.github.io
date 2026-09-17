## 配置文件位置

```
# debian 12及之前版本
/etc/apt/sources.list
/etc/apt/sources.list.d/*.list

# debian 13+
/etc/apt/sources.list.d/*.sources
```

## 配置文件内容

### Debian 13 (Trixie)

```
deb https://deb.debian.org/debian trixie main
deb https://deb.debian.org/debian-security trixie-security main
deb https://deb.debian.org/debian/ trixie-updates main

```

### Debian 12 (Bookworm)

```
deb http://deb.debian.org/debian bookworm main contrib non-free-firmware non-free
deb http://deb.debian.org/debian bookworm-updates main contrib non-free-firmware non-free
deb http://security.debian.org/debian-security bookworm-security main contrib non-free-firmware non-free

```

### Debian 11 (Bullseye)

```
deb http://archive.debian.org/debian bullseye main contrib non-free
deb http://archive.debian.org/debian bullseye-updates main contrib non-free

```

### Debian 10 (Buster)

```
deb http://archive.debian.org/debian/ buster main contrib non-free
deb http://archive.debian.org/debian/ buster-proposed-updates main contrib non-free
deb http://archive.debian.org/debian-security buster/updates main contrib non-free

```

### Debian 9 (Stretch)

```
deb http://archive.debian.org/debian/ stretch main contrib non-free
deb http://archive.debian.org/debian/ stretch-proposed-updates main contrib non-free
deb http://archive.debian.org/debian-security stretch/updates main contrib non-free

```

### Debian 8 (Jessie)

```
deb http://archive.debian.org/debian/ jessie main contrib non-free
deb http://archive.debian.org/debian-security jessie/updates main contrib non-free

```

### Debian 7  (Wheezy) 

```
deb http://archive.debian.org/debian/ wheezy main contrib non-free
deb http://archive.debian.org/debian-security wheezy/updates main contrib non-free

```

## 常用命令

### 升级

```shell
sudo apt update
```

### 包名称搜索

```shell
sudo apt search --names-only '^default-jre$'

```

### 查看包明细

```shell
sudo apt show '^default-jre$'

```

### 查看包依赖

```shell
sudo apt depends '^default-jre$'
```

### 安装包

```shell
sudo apt install --no-install-recommends -y -s --download-only --auto-remove '^default-jre$'

# --no-install-recommends 不安装推荐包
# -y 自动确认
# -s 模拟安装
# --download-only 仅下载
# --auto-remove 安装后自动移除不再需要的依赖
```

### 查看已安装包

```shell
sudo apt list --installed

```

### 删除包

```shell
sudo apt remove default-jre

```

### 删除包及配置文件

```shell
sudo apt purge --autoremove mysql-common

# --autoremove 删除依赖
```

### **清理所有不再需要的依赖**

```shell
sudo apt autoremove --purge
# TODO
```

### 格式转换

```shell
sudo apt modernize-sources

# APT 版本（2.9.26 及以上）自动将 /etc/apt/sources.list 和 /etc/apt/sources.list.d/ 下的 .list 文件转换为 .sources 格式，并将原文件备份为 .list.bak。
```

### 查看APT版本

```shell
sudo apt -v
```

### **清理 APT 缓存**

```shell
sudo apt clean
```

