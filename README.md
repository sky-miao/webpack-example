#### webpack 构建工具
#### 在项目根目录下运行：
    * npm init -y
#### 搭建基本的项目结构如下
    - webpack-example
        - dist   打包后的文件
        - src
            - js
                - app.js
        - .gitignore 不提交git的文件
        - package.json
        - README.md
        - webpack.develop.config.js
        - webpack.publish.config.js
#### 安装
    * npm install webpack -g
    * npm install webpack -save-dev
    * npm install react -save
#### 配置问件 （webpack.develop.config.js）
```
// webpack 的开发配置文件
// 编写配置文件，要有最基本的文件入口和输出文件配置信息等
// 里面还可以加loader和各种插件配置使用
var path = require('path');
module.exports = {
    // 单页面 SPA 的入口文件
    entry:path.resolve(__dirname,'src/js/app.js'),
    // 构建之后的文件输出位置配置
    output: {
        path: path.resolve(__dirname, 'dist'),
        filename: 'bundle.js'
    }
};
```
#### 运行
    * webpack --config webpack.develop.config.js
    * 可看到dist中的bundle.js文件



#### webpack 启动过程演进
    + package.json
    ```
    "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1",
        "develop": "webpack --config webpack.develop.config.js",
        "publish": "webpack --config webpack.publish.config.js"
    }
    ```
    * 执行 ：npm run develop
###### 安装第三方 自动监听插件
    * npm install webpack-dev-server -save-dev
    + package.json
    ```
    "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1",
        "develop": "webpack-dev-server --config webpack.develop.config.js --devtool eval --progress --colors --hot --content-base src",
        "publish": "webpack --config webpack.publish.config.js"
    }
    ```
    * webpack-dev-server - 在 localhost:8080 建立一个 Web 服务器
    * –devtool eval - 为你的代码创建源地址。当有任何报错的时候可以让你更加精确地定位到文件和行号
    * –progress - 显示合并代码进度
    * –colors – hot，命令行中显示颜色！
    * –content-base 指向设置的输出目录//这点一定是我们的发布目录
    
##### index.html
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>webpack 使用</title>
</head>
<body>
    <div id="app"> hello world </div>
</body>
<script src="bundle.js"></script>
</html>
```
##### 执行
    * npm run develop 
    * 启动监听，并在 8080 端口开启了一个服务器。
    
    * 注意:
        1. 用 webpack-dev-server 生成 bundle.js 文件是在内存中的，并没有实际生成
        2. 如果引用的文件夹中已经有 bundle.js 就不会自动刷新了，你需要先把 bundle.js 文件手动删除
        3. 用 webstorm 需要注意，因为他是自动保存的，所以可能识别的比较慢，你需要手动的 ctrl+s 一下
