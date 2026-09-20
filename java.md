### 解压

```shell
sudo tar zxf openjdk-11.0.2_linux-x64_bin.tar.gz -C /srv
```

### 设置环境变量

```shell
sudo nano /etc/profile

# 追加内容
export JAVA_HOME="/srv/jdk-11.0.2"
export PATH="$JAVA_HOME/bin:$PATH"

# 设置生效
sudo source /etc/profile

# 检查状态
java -version
## 输出内容
openjdk version "11.0.2" 2019-01-15
OpenJDK Runtime Environment 18.9 (build 11.0.2+9)
OpenJDK 64-Bit Server VM 18.9 (build 11.0.2+9, mixed mode)

```

