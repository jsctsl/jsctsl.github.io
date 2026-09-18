## 自动化仓库配置

```shell
sudo apt install -y postgresql-common

```

```
Get:1 http://mirrors.cloud.aliyuncs.com/debian trixie InRelease [140 kB]
Get:2 http://mirrors.cloud.aliyuncs.com/debian trixie-updates InRelease [47.3 kB]
Get:3 http://mirrors.cloud.aliyuncs.com/debian trixie-backports InRelease [54.0 kB]
Get:4 http://mirrors.cloud.aliyuncs.com/debian-security trixie-security InRelease [43.4 kB]
Get:5 http://mirrors.cloud.aliyuncs.com/debian trixie/main Sources [10.5 MB]
Get:6 http://mirrors.cloud.aliyuncs.com/debian trixie/main amd64 Packages [9,678 kB]
Get:7 http://mirrors.cloud.aliyuncs.com/debian trixie/main Translation-en [6,486 kB]
Get:8 http://mirrors.cloud.aliyuncs.com/debian trixie-updates/main Sources [1,840 B]
Get:9 http://mirrors.cloud.aliyuncs.com/debian trixie-updates/main amd64 Packages [4,412 B]
Get:10 http://mirrors.cloud.aliyuncs.com/debian trixie-updates/main Translation-en [2,496 B]
Get:11 http://mirrors.cloud.aliyuncs.com/debian trixie-backports/main Sources [311 kB]
Get:12 http://mirrors.cloud.aliyuncs.com/debian trixie-backports/main amd64 Packages [324 kB]
Get:13 http://mirrors.cloud.aliyuncs.com/debian trixie-backports/main Translation-en [237 kB]
Get:14 http://mirrors.cloud.aliyuncs.com/debian-security trixie-security/main Sources [230 kB]
Get:15 http://mirrors.cloud.aliyuncs.com/debian-security trixie-security/main amd64 Packages [262 kB]
Get:16 http://mirrors.cloud.aliyuncs.com/debian-security trixie-security/main Translation-en [160 kB]
Fetched 28.5 MB in 3s (10.3 MB/s)                              
123 packages can be upgraded. Run 'apt list --upgradable' to see them.
root@iZv6yj98prgnznZ:/etc/apt/sources.list.d# sudo apt install -y postgresql-common
Installing:                     
  postgresql-common

Installing dependencies:
  libcommon-sense-perl  libio-pty-perl  libipc-run-perl  libjson-perl  libjson-xs-perl  libtypes-serialiser-perl  postgresql-client-common  postgresql-common-dev  ssl-cert

Summary:
  Upgrading: 0, Installing: 10, Removing: 0, Not Upgrading: 123
  Download size: 597 kB
  Space needed: 1,847 kB / 37.8 GB available

Get:1 http://mirrors.cloud.aliyuncs.com/debian trixie/main amd64 libjson-perl all 4.10000-1 [87.5 kB]
Get:2 http://mirrors.cloud.aliyuncs.com/debian trixie/main amd64 postgresql-client-common all 278 [47.1 kB]
Get:3 http://mirrors.cloud.aliyuncs.com/debian trixie/main amd64 libio-pty-perl amd64 1:1.20-1+b3 [34.3 kB]
Get:4 http://mirrors.cloud.aliyuncs.com/debian trixie/main amd64 libipc-run-perl all 20231003.0-2 [101 kB]
Get:5 http://mirrors.cloud.aliyuncs.com/debian trixie/main amd64 postgresql-common-dev all 278 [72.4 kB]
Get:6 http://mirrors.cloud.aliyuncs.com/debian trixie/main amd64 ssl-cert all 1.1.3 [16.8 kB]
Get:7 http://mirrors.cloud.aliyuncs.com/debian trixie/main amd64 postgresql-common all 278 [112 kB]
Get:8 http://mirrors.cloud.aliyuncs.com/debian trixie/main amd64 libcommon-sense-perl amd64 3.75-3+b5 [22.9 kB]
Get:9 http://mirrors.cloud.aliyuncs.com/debian trixie/main amd64 libtypes-serialiser-perl all 1.01-1 [12.2 kB]
Get:10 http://mirrors.cloud.aliyuncs.com/debian trixie/main amd64 libjson-xs-perl amd64 4.040-1~deb13u1 [91.0 kB]
Fetched 597 kB in 0s (4,336 kB/s)           
Preconfiguring packages ...
Selecting previously unselected package libjson-perl.
(Reading database ... 56737 files and directories currently installed.)
Preparing to unpack .../0-libjson-perl_4.10000-1_all.deb ...
Unpacking libjson-perl (4.10000-1) ...
Selecting previously unselected package postgresql-client-common.
Preparing to unpack .../1-postgresql-client-common_278_all.deb ...
Unpacking postgresql-client-common (278) ...
Selecting previously unselected package libio-pty-perl.
Preparing to unpack .../2-libio-pty-perl_1%3a1.20-1+b3_amd64.deb ...
Unpacking libio-pty-perl (1:1.20-1+b3) ...
Selecting previously unselected package libipc-run-perl.
Preparing to unpack .../3-libipc-run-perl_20231003.0-2_all.deb ...
Unpacking libipc-run-perl (20231003.0-2) ...
Selecting previously unselected package postgresql-common-dev.
Preparing to unpack .../4-postgresql-common-dev_278_all.deb ...
Unpacking postgresql-common-dev (278) ...
Selecting previously unselected package ssl-cert.
Preparing to unpack .../5-ssl-cert_1.1.3_all.deb ...
Unpacking ssl-cert (1.1.3) ...
Selecting previously unselected package postgresql-common.
Preparing to unpack .../6-postgresql-common_278_all.deb ...
Adding 'diversion of /usr/bin/pg_config to /usr/bin/pg_config.libpq-dev by postgresql-common'
Unpacking postgresql-common (278) ...
Selecting previously unselected package libcommon-sense-perl:amd64.
Preparing to unpack .../7-libcommon-sense-perl_3.75-3+b5_amd64.deb ...
Unpacking libcommon-sense-perl:amd64 (3.75-3+b5) ...
Selecting previously unselected package libtypes-serialiser-perl.
Preparing to unpack .../8-libtypes-serialiser-perl_1.01-1_all.deb ...
Unpacking libtypes-serialiser-perl (1.01-1) ...
Selecting previously unselected package libjson-xs-perl.
Preparing to unpack .../9-libjson-xs-perl_4.040-1~deb13u1_amd64.deb ...
Unpacking libjson-xs-perl (4.040-1~deb13u1) ...
Setting up postgresql-client-common (278) ...
Setting up libio-pty-perl (1:1.20-1+b3) ...
Setting up libcommon-sense-perl:amd64 (3.75-3+b5) ...
Setting up ssl-cert (1.1.3) ...
Setting up libipc-run-perl (20231003.0-2) ...
Setting up libtypes-serialiser-perl (1.01-1) ...
Setting up libjson-perl (4.10000-1) ...
Setting up postgresql-common-dev (278) ...
Setting up libjson-xs-perl (4.040-1~deb13u1) ...
Setting up postgresql-common (278) ...
Creating config file /etc/postgresql-common/createcluster.conf with new version
Building PostgreSQL dictionaries from installed myspell/hunspell packages...
Removing obsolete dictionary files:
Created symlink '/etc/systemd/system/multi-user.target.wants/postgresql.service' → '/usr/lib/systemd/system/postgresql.service'.
Processing triggers for man-db (2.13.1-1) ...
```



```shell
sudo /usr/share/postgresql-common/pgdg/apt.postgresql.org.sh

```

```
This script will enable the PostgreSQL APT repository on apt.postgresql.org on
your system. The distribution codename used will be trixie-pgdg.

Press Enter to continue, or Ctrl-C to abort.

Using keyring /usr/share/postgresql-common/pgdg/apt.postgresql.org.gpg
Writing /etc/apt/sources.list.d/pgdg.sources ...

Running apt-get update ...
Hit:1 http://mirrors.cloud.aliyuncs.com/debian trixie InRelease
Hit:2 http://mirrors.cloud.aliyuncs.com/debian trixie-updates InRelease
Hit:3 http://mirrors.cloud.aliyuncs.com/debian trixie-backports InRelease
Hit:4 http://mirrors.cloud.aliyuncs.com/debian-security trixie-security InRelease
Get:5 https://apt.postgresql.org/pub/repos/apt trixie-pgdg InRelease [241 kB]
Get:6 https://apt.postgresql.org/pub/repos/apt trixie-pgdg/main amd64 Packages [857 kB]                                                                                                                 
Fetched 1,098 kB in 1min 13s (15.1 kB/s)                                                                                                                                                                
Reading package lists... Done

You can now start installing packages from apt.postgresql.org.

Have a look at https://wiki.postgresql.org/wiki/Apt for more information;
most notably the FAQ at https://wiki.postgresql.org/wiki/Apt/FAQ
```

### 安装

```shell
apt install --no-install-recommends -y 'postgresql-16'

# --auto-remove 
```

```
Installing:                     
  postgresql-16

Installing dependencies:
  libicu76  libllvm19  libpq5  libxslt1.1  libz3-4  postgresql-client-16

Suggested packages:
  libpq-oauth  postgresql-doc-16

Summary:
  Upgrading: 0, Installing: 7, Removing: 0, Not Upgrading: 123
  Download size: 62.9 MB
  Space needed: 265 MB / 37.7 GB available

Continue? [Y/n] y
Get:1 http://mirrors.cloud.aliyuncs.com/debian trixie/main amd64 libicu76 amd64 76.1-4 [9,722 kB]
Get:2 http://mirrors.cloud.aliyuncs.com/debian trixie/main amd64 libz3-4 amd64 4.13.3-1 [8,560 kB]
Get:3 http://mirrors.cloud.aliyuncs.com/debian trixie/main amd64 libllvm19 amd64 1:19.1.7-3+b1 [26.0 MB]
Get:4 http://mirrors.cloud.aliyuncs.com/debian trixie/main amd64 libxslt1.1 amd64 1.1.35-1.2+deb13u3 [233 kB]
Get:5 https://apt.postgresql.org/pub/repos/apt trixie-pgdg/main amd64 libpq5 amd64 18.6-1.pgdg13+2 [266 kB]
Get:6 https://apt.postgresql.org/pub/repos/apt trixie-pgdg/main amd64 postgresql-client-16 amd64 16.15-1.pgdg13+2 [1,973 kB]
Get:7 https://apt.postgresql.org/pub/repos/apt trixie-pgdg/main amd64 postgresql-16 amd64 16.15-1.pgdg13+2 [16.1 MB]                                                                                    
Fetched 62.9 MB in 14min 24s (72.8 kB/s)                                                                                                                                                                
Preconfiguring packages ...
Selecting previously unselected package libicu76:amd64.
(Reading database ... 56921 files and directories currently installed.)
Preparing to unpack .../0-libicu76_76.1-4_amd64.deb ...
Unpacking libicu76:amd64 (76.1-4) ...
Selecting previously unselected package libz3-4:amd64.
Preparing to unpack .../1-libz3-4_4.13.3-1_amd64.deb ...
Unpacking libz3-4:amd64 (4.13.3-1) ...
Selecting previously unselected package libllvm19:amd64.
Preparing to unpack .../2-libllvm19_1%3a19.1.7-3+b1_amd64.deb ...
Unpacking libllvm19:amd64 (1:19.1.7-3+b1) ...
Selecting previously unselected package libpq5:amd64.
Preparing to unpack .../3-libpq5_18.6-1.pgdg13+2_amd64.deb ...
Unpacking libpq5:amd64 (18.6-1.pgdg13+2) ...
Selecting previously unselected package libxslt1.1:amd64.
Preparing to unpack .../4-libxslt1.1_1.1.35-1.2+deb13u3_amd64.deb ...
Unpacking libxslt1.1:amd64 (1.1.35-1.2+deb13u3) ...
Selecting previously unselected package postgresql-client-16.
Preparing to unpack .../5-postgresql-client-16_16.15-1.pgdg13+2_amd64.deb ...
Unpacking postgresql-client-16 (16.15-1.pgdg13+2) ...
Selecting previously unselected package postgresql-16.
Preparing to unpack .../6-postgresql-16_16.15-1.pgdg13+2_amd64.deb ...
Unpacking postgresql-16 (16.15-1.pgdg13+2) ...
Setting up libpq5:amd64 (18.6-1.pgdg13+2) ...
Setting up libz3-4:amd64 (4.13.3-1) ...
Setting up libxslt1.1:amd64 (1.1.35-1.2+deb13u3) ...
Setting up libicu76:amd64 (76.1-4) ...
Setting up libllvm19:amd64 (1:19.1.7-3+b1) ...
Setting up postgresql-client-16 (16.15-1.pgdg13+2) ...
update-alternatives: using /usr/share/postgresql/16/man/man1/psql.1.gz to provide /usr/share/man/man1/psql.1.gz (psql.1.gz) in auto mode
Setting up postgresql-16 (16.15-1.pgdg13+2) ...
Creating new PostgreSQL cluster 16/main ...
/usr/lib/postgresql/16/bin/initdb -D /var/lib/postgresql/16/main --auth-local peer --auth-host scram-sha-256 --no-instructions
The files belonging to this database system will be owned by user "postgres".
This user must also own the server process.

The database cluster will be initialized with locale "en_US.UTF-8".
The default database encoding has accordingly been set to "UTF8".
The default text search configuration will be set to "english".

Data page checksums are disabled.

fixing permissions on existing directory /var/lib/postgresql/16/main ... ok
creating subdirectories ... ok
selecting dynamic shared memory implementation ... posix
selecting default max_connections ... 100
selecting default shared_buffers ... 128MB
selecting default time zone ... Asia/Shanghai
creating configuration files ... ok
running bootstrap script ... ok
performing post-bootstrap initialization ... ok
syncing data to disk ... ok
Processing triggers for postgresql-common (293.pgdg13+1) ...
Building PostgreSQL dictionaries from installed myspell/hunspell packages...
Removing obsolete dictionary files:
Processing triggers for libc-bin (2.41-12+deb13u2) ...

```


```
Creating new PostgreSQL cluster 16/main ...
/usr/lib/postgresql/16/bin/initdb -D /var/lib/postgresql/16/main --auth-local peer --auth-host scram-sha-256 --no-instructions
The files belonging to this database system will be owned by user "postgres".
This user must also own the server process.

The database cluster will be initialized with locale "en_US.UTF-8".
The default database encoding has accordingly been set to "UTF8".
The default text search configuration will be set to "english".

Data page checksums are disabled.

fixing permissions on existing directory /var/lib/postgresql/16/main ... ok
creating subdirectories ... ok
selecting dynamic shared memory implementation ... posix
selecting default max_connections ... 100
selecting default shared_buffers ... 128MB
selecting default time zone ... Asia/Shanghai
creating configuration files ... ok
running bootstrap script ... ok
performing post-bootstrap initialization ... ok
syncing data to disk ... ok
Ver Cluster Port Status Owner    Data directory              Log file
16  main    5432 down   postgres /var/lib/postgresql/16/main /var/log/postgresql/postgresql-16-main.log

```



### 配置

#### 监听地址

```shell
cat /etc/postgresql/16/main/postgresql.conf | grep '#listen'
#listen_addresses = 'localhost'		# what IP address(es) to listen on;

# TO
listen_addresses = '*'		# what IP address(es) to listen on;
```

#### 内网远程登录

```shell
echo 'host all all 192.168.200.0/24 scram-sha-256' >> /etc/postgresql/16/main/pg_hba.conf

# /etc/fstab 文件追加下行内容
# host all all 192.168.200.0/24 scram-sha-256
```

#### 修改密码

```
sudo -u postgres psql

psql (16.15 (Debian 16.15-1.pgdg13+2))
Type "help" for help.

postgres=# alter user postgres with password 'XXXX';
ALTER ROLE

```

#### 检查修改结果

```
sudo -u postgres psql

psql (16.15 (Debian 16.15-1.pgdg13+2))
Type "help" for help.

postgres=# select usename, passwd from pg_shadow;
 usename  |                                                                passwd                                                                 
----------+---------------------------------------------------------------------------------------------------------------------------------------
 postgres | SCRAM-SHA-256$4096:38Im5tIKv98s4MTzAhL6BQ==$7ZseaybUTliiQUPdtq9bSRxCFFWCJC4i+tvITFIj5o4=:PlTANsrutdC3mQbTMfUEVTQBEHeMPtuG7yBvi2wYoPQ=
(1 row)
```

#### 修改数据目录
```
mkdir -p /data/postgresql/16/main
chown postgres:postgres /data/postgresql/16/main
chmod 700 /data/postgresql/16/main

mv /var/lib/postgresql/16/main/* /data/postgresql/16/main

nano /etc/fstab
  /data/postgresql/16/main /var/lib/postgresql/16/main none bind 0 0

reboot
```


### 备份

```
cd /data/backup

# 备份数据库 james 为文件 james.dump 
# -F c 自定义文件格式
# -O 跳过所有者设置 (不执行 ALTER ... OWNER TO ... 这类语句)
# -f james.dump 备份文件
# -d james 数据库名称
sudo pg_dump -h localhost -p 5432 -U postgres -F c -O -f james.dump -d james


# =============
# && gzip -kf james.tar 备份成功后再压缩
sudo pg_dump -h localhost -p 5432 -U postgres -F t -O -f james.tar -d james && gzip -kf james.tar

```

### 恢复

```
sudo -u postgres psql

# LOGIN 登录权限
# NOSUPERUSER 非超级用户
# INHERIT 从父类继承权限
# CREATEDB 创建数据库权限
# NOCREATEROLE 无创建角色权限
# REPLICATION 复制备份权限
# PASSWORD 密码
CREATE ROLE jamesmail WITH
  LOGIN
  NOSUPERUSER
  INHERIT
  CREATEDB
  NOCREATEROLE
  REPLICATION
  PASSWORD 'XXXX';

# --role=jamesmail 
# -v -v 输出更详细的调试信息(并非所有版本都支持) OR 使用 --verbose 选项
# -C -d postgres 使用备份文件中的创建数据库命令 -d postgres 作为跳板连接数据库使用
# james.dump 备份文件
pg_restore -h localhost -p 5432 -U postgres -F c --role=jamesmail -v -v -C -d postgres james.dump 
```


## ~~禁用集群~~
```shell
cat /etc/postgresql-common/createcluster.conf | grep '^create_main_cluster';
#create_main_cluster = true

nano /etc/postgresql-common/createcluster.conf
create_main_cluster = false

```


## ~~创建集群~~

```shell
sudo pg_createcluster 16 main
```