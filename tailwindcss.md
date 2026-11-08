### Installation

#### Tailwind CLI

```
chensheng@ChenShengdeMacBook-Pro ~ % cd /Users/chensheng/Git/demos/tailwindcss4

chensheng@ChenShengdeMacBook-Pro tailwindcss4 % npm install tailwindcss @tailwindcss/cli

added 28 packages in 2m

7 packages are looking for funding
  run `npm fund` for details
npm notice
npm notice New major version of npm available! 10.9.9 -> 12.2.2
npm notice Changelog: https://github.com/npm/cli/releases/tag/v12.2.2
npm notice To update run: npm install -g npm@12.2.2
npm notice

chensheng@ChenShengdeMacBook-Pro tailwindcss4 % mkdir src
chensheng@ChenShengdeMacBook-Pro tailwindcss4 % nano src/input.css
@import "tailwindcss";

chensheng@ChenShengdeMacBook-Pro tailwindcss4 % nano src/index.html
<!doctype html>
<html>
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link href="../dist/output.css" rel="stylesheet">
</head>
<body>
  <h1 class="text-3xl font-bold underline">
    Hello world!
  </h1>
</body>
</html>

# CSS
chensheng@ChenShengdeMacBook-Pro tailwindcss4 % npx @tailwindcss/cli -i ./src/input.css -o ./dist/output.css --watch


# 优化
chensheng@ChenShengdeMacBook-Pro tailwindcss4 % npm uninstall @tailwindcss/cli html-minifier-terser
chensheng@ChenShengdeMacBook-Pro tailwindcss4 % npm install @tailwindcss/cli -D
chensheng@ChenShengdeMacBook-Pro tailwindcss4 % nano package.json
# package.json
......
  "main": "index.html",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "watch:css": "npx @tailwindcss/cli -i ./src/input.css -o ./dist/output.css --watch",
    "build:css": "npx @tailwindcss/cli -i ./src/input.css -o ./dist/output.css",
    "build:html": "html-minifier-terser --collapse-whitespace --remove-comments --output dist/index.html src/index.html",
    "build": "npm run build:html && npm run build:css"
  },
......  
  "dependencies": {
    "tailwindcss": "^4.3.5"
  },
  "devDependencies": {
    "@tailwindcss/cli": "^4.3.5",
    "html-minifier-terser": "^7.2.0"
  }
  
chensheng@ChenShengdeMacBook-Pro tailwindcss4 % npm run watch:css
```

