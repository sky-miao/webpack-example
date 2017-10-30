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


