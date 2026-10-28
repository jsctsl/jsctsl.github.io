### 启动菜单位置

```
win+r

-- All Users / System-wide
-- C:\ProgramData\Microsoft\Windows\Start Menu\Programs\StartUp
shell:common startup

-- Per-user
-- %USERPROFILE%\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup
shell:startup
```

### 端口占用查询

```
netstat -ano | findstr 3306
```
