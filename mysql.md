### 备份

```
c:\mysql\bin\mysqldump.exe -u root -p test > test.sql

备份数据库 test 到sql脚本文件

c:\mysql\bin\mysqldump.exe -u root -p test user > test_user.sql
备份表 user 到sql脚本文件
```

### 恢复

```
C:\mysql\bin>mysql -u root -p test1 < test.sql

恢复数据库 test1 使用sql脚本文件
```

### 忘记密码

```
1、启动数据库服务(无权限认证)
C:\mysql\bin>mysqld.exe --console --skip-grant-tables --shared-memory

2、登录数据库并更新密码
C:\mysql\bin>mysql.exe -u root -p mysql
mysql> update user set authentication_string = password('Qwas!290') where user='root' and Host='localhost';
mysql> flush privileges;
mysql> quit;
```

