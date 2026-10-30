### Debian 或 Ubuntu 上安装 Deb

[参考文档](https://adoptium.net/zh-CN/installation/linux#_deb_installation_on_debian_or_ubuntu)

```
### 必要的软件包
apt install -y wget apt-transport-https gpg

### 下载 Eclipse Adoptium GPG 密钥
wget -qO - https://packages.adoptium.net/artifactory/api/gpg/key/public | gpg --dearmor | tee /etc/apt/trusted.gpg.d/adoptium.gpg > /dev/null

### 配置 Eclipse Adoptium apt 存储库
echo "deb https://packages.adoptium.net/artifactory/deb $(awk -F= '/^VERSION_CODENAME/{print$2}' /etc/os-release) main" | tee /etc/apt/sources.list.d/adoptium.list

### 安装您需要的 Temurin 版本
apt update
apt install|search temurin-<version>-jdk


```

```
#!/bin/bash
nohup java -jar /usr/local/bin/mailquartz.jar >> /usr/local/bin/mailquartz.log 2>&1 &
echo $! > mailquartz.pid

kill $(cat mailquartz.pid)
```


```
useradd -s /sbin/nologin jansc

touch /etc/systemd/system/mailquartz.service


[Unit]
Description=Mail Quartz Daemon Service
After=network.target

[Service]
Type=simple
# 建议使用非root用户
User=jansc
# 脚本所在目录
WorkingDirectory=/usr/local/bin
# 脚本的绝对路径
ExecStart=/usr/local/bin/mailquartz.sh
# 失败时自动重启
Restart=on-failure
# 重启间隔
RestartSec=10s

[Install]
WantedBy=multi-user.target

```


```
systemctl daemon-reload
systemctl enable --now mailquartz.service
```

