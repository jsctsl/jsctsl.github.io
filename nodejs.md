### partable

```

```

### http server

```
# C:\Users\chensheng\WebstormProjects\nodejs\app.js

const http = require('http');

const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader('Content-Type', 'text/plain');
  res.end(' RUNOOB Node Test ~ Hello, Node.js!\n');
});

const port = 3000;
server.listen(port, () => {
  console.log(`服务器运行地址：http://localhost:${port}/`);
});


# C:\Users\chensheng\WebstormProjects\nodejs>node app.js
# HTTP 服务器已启动：http://localhost:3000

# 浏览器访问 http://localhost:3000
```

### https server

```
证书文件内容参考 keytool.md

# C:\Users\chensheng\WebstormProjects\nodejs\app.js

const https = require('https');
const fs = require('fs');
const path = require('path');

// 1. 读取 p12 文件并配置参数
const options = {
  // 读取 p12 二进制数据
  pfx: fs.readFileSync(path.join(__dirname, 'keystore.p12')), 
  // 如果你的 p12 文件有密码保护，请填入密码；若无密码，可省略该字段
  passphrase: '12345678' 
};

// 2. 创建 HTTPS 服务器
const server = https.createServer(options, (req, res) => {
  res.writeHead(200, { 'Content-Type': 'text/plain; charset=utf-8' });
  res.end('HTTPS 服务器已通过 p12 文件成功运行！');
});

// 3. 监听端口
const PORT = 3000;
server.listen(PORT, () => {
  console.log(`HTTPS 服务器已启动：https://localhost:${PORT}`);
});

# C:\Users\chensheng\WebstormProjects\nodejs>set NODE_OPTIONS="--openssl-legacy-provider"
# C:\Users\chensheng\WebstormProjects\nodejs>node app.js
# HTTP 服务器已启动：http://localhost:3000

# 浏览器访问 https://localhost:3000
```

### macOS

```
pkg 安装路径
Node.js v24.22.2 to /usr/local/bin/node
npm v11.19.1 to /usr/local/bin/npm

```

### 插件

```
# HTML 压缩
chensheng@ChenShengdeMacBook-Pro tailwindcss4 % npm install -D html-minifier-terser


```

