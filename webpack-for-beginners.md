## Webpack给初学者
### Webpack是什么？
Webpack是一个模块打包和压缩工具
### 什么是模块打包？
模块打包就是把多个Javascript文件打包和压缩成一个单独的Javascript文件
### 怎样使用？
####开始创建一个项目
```
$ mkdir try-webpack && cd try-webpack && mkdir src && npm init -y
$ touch index.html && touch src/main.js && touch webpack.config.js
```
如果你是Windows用户，可以通过<a href="https://git-scm.com/downloads" target="_blank">git bash</a>运行上面的命令。现在我们开始全局安装webpack:
```
$ npm install -g webpack
```
####我们通过一个简单的配置文件开始我们所有的前端项目，打开```webpack.config.js```文件，复制下面的代码粘贴到```webpack.config.js```中
```
module.exports = {
  devtool: 'cheap-module-eval-source-map',
  entry: "./src/main.js",
  output: {
    path: __dirname + "/dist",
    filename: "bundle.js"
  }
};
```
这个文件告诉webpack我们的应用入口点在哪里以及在哪个目录输出打包后的代码，通过命令行运行```webpack```,在dist目录下就会生成bundle.js文件。
