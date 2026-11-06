### 生成密钥库

```
keytool -genkeypair \
  -alias jsc.local.me \
  -keyalg RSA \
  -keysize 4096 \
  -validity 3650 \
  -keystore keystore.p12 \
  -storetype PKCS12 \
  -storepass 12345678 \
  -dname "CN=jsc.local.me, OU=IT, O=jsc.local.me, L=ZhenJiang, ST=JiangSu, C=CN" \
  -ext "san=dns:jsc.local.me,ip:192.168.200.222"



# 自定义域名文件 C:\Windows\System32\drivers\etc\hosts
```

### 导出证书

```
keytool -exportcert \
  -alias jsc.local.me \
  -keystore keystore.p12 \
  -storepass 12345678 \
  -file jsc.local.me.crt \
  -rfc
```

### 导入证书

```
Windows 上的 Chrome 默认使用系统的证书存储。
1. 打开证书管理器：按下 Win + R 键，输入 certmgr.msc 并回车。
2. 定位到目标文件夹：在左侧导航栏中，展开 “受信任的根证书颁发机构”，然后右键点击其下的 “证书” 文件夹。
3. 导入证书：选择 “所有任务” -> “导入”。
4. 选择文件：点击“下一步”，浏览并选择你的自签发 根证书文件（通常是 .crt、.cer 或 .pfx 格式）。
5. 确认存储位置：确保证书存储路径显示为“受信任的根证书颁发机构”，点击“下一步”直至“完成”。
6. 重启浏览器：彻底关闭并重新打开 Chrome 浏览器即可生效

macOS //TBV
Mac 上的 Chrome 使用系统的“钥匙串访问”来管理证书。
1. 打开钥匙串：在 Mac 上打开 “钥匙串访问” (Keychain Access) 应用程序。
2. 导入证书：选择左侧的 “登录” 或 “系统” 钥匙串，将你的 .crt 证书文件直接拖拽到右侧列表中。
3. 修改信任设置：双击刚刚导入的证书，展开 “信任” (Trust) 选项。
4. 设为始终信任：将“使用此证书时” (When using this certificate) 下拉菜单修改为 “始终信任” (Always Trust)。
5. 保存：关闭窗口并输入 Mac 的开机密码确认修改，重启 Chrome。

Chrome //TBV
如果你使用的是 Linux，或者想直接通过浏览器界面操作：
1. 打开 Chrome，在地址栏输入 chrome://settings/security 并回车。
2. 向下滚动并点击 “管理证书”。
3. 在弹出的本地管理界面中，切换到 “受信任的根证书颁发机构”（或 Authorities/证书颁发机构）标签页。
4. 点击 “导入”，选择你的 CA 证书并按照提示勾选“信任此证书用于标识网站”，完成导入并重启浏览器。


极简开发替代方案 //TBV
如果你在本地开发时，纯粹是为了让 https://localhost 在 Chrome 中不报错，而不想折腾复杂的 Java 密钥库和代码，最痛快的工具其实是本地 CA 工具 mkcert。
1. 运行 mkcert -install（它会自动在你的操作系统和 Chrome 中安装一个本地根证书）。
2. 运行 mkcert localhost 127.0.0.1（直接生成现成可用的本地 HTTPS 证书，100% 完美适配 Chrome）。
```

