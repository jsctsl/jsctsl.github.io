
### 前提

```
# 建用户
-- Role: james
-- DROP ROLE IF EXISTS james;

CREATE ROLE james WITH
  LOGIN
  NOSUPERUSER
  INHERIT
  CREATEDB
  NOCREATEROLE
  NOREPLICATION
  NOBYPASSRLS
  PASSWORD 'XXXX';

# 建库
-- Database: james

-- DROP DATABASE IF EXISTS james;

CREATE DATABASE james
    WITH
    OWNER = james
    ENCODING = 'UTF8'
    LC_COLLATE = 'en_US.UTF-8'
    LC_CTYPE = 'en_US.UTF-8'
    LOCALE_PROVIDER = 'libc'
    TABLESPACE = pg_default
    CONNECTION LIMIT = -1
    IS_TEMPLATE = False;
```


### 解压

```
unzip james-server-jpa-guice.zip -d /srv
```

### 创建用户

```
adduser --system --group --no-create-home james
```

### 授权

```
chown -R james:james /srv/james-server-jpa-guice
```

### 服务脚本

```
nano /usr/lib/systemd/system/james.service
```

```
# 脚本内容
[Unit]
Description=Apache James Mail Server
After=network.target
#After=network.target postgresql.service
#Wants=postgresql.service
#Requires=postgresql.service

[Service]
Type=simple
# 建议使用非 root 用户运行服务以提高安全性
User=james
Group=james
# James 的安装目录
WorkingDirectory=-/srv/james-server-jpa-guice
# 启动命令，根据实际 Java 路径和 Jar 包名称调整
ExecStartPre=/usr/bin/sleep 120
TimeoutStartSec=180
# ExecStart=/srv/james-server-jpa-guice/startup.sh
ExecStart=/srv/jdk-11.0.2/bin/java -javaagent:james-server-jpa-app.lib/openjpa-3.2.0.jar -Dworking.directory=. -Djdk.tls.ephemeralDHKeySize=2048 -Dlogback.configurationFile=conf/logback.xml -Duser.timezone=Asia/Shanghai -jar james-server-jpa-app.jar
# 如果服务意外退出，自动重启
Restart=always
RestartSec=300
# 提权(小于1024的端口)
AmbientCapabilities=CAP_NET_BIND_SERVICE

[Install]
WantedBy=multi-user.target

```

### 自启动

```
systemctl daemon-reload
systemctl enable

systemctl start james

# 检查启动错误
journalctl -xeu james.service
```
