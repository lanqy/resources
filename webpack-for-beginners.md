## Webpack给初学者
### Webpack是什么？
Webpack是一个模块打包和压缩工具
### 什么是模块打包？
模块打包就是把多个Javascript文件打包和压缩成一个单独的Javascript文件
### 怎样使用？
####开始创建一个项目
```shell
$ mkdir try-webpack && cd try-webpack && mkdir src && npm init -y
$ touch index.html && touch src/main.js && touch webpack.config.js
```
如果你是Windows用户，可以通过<a href="https://git-scm.com/downloads" target="_blank">git bash</a>运行上面的命令。现在我们开始全局安装webpack:
```
$ npm install -g webpack
```
我们通过一个简单的配置文件开始我们所有的前端项目，打开```webpack.config.js```文件，复制下面的代码粘贴到```webpack.config.js```中
```javascript
module.exports = {
  devtool: 'cheap-module-eval-source-map',
  entry: "./src/main.js",
  output: {
    path: __dirname + "/dist",
    filename: "bundle.js"
  }
};
```

这个文件告诉webpack我们的应用入口点在哪里以及在哪个目录输出打包后的代码，通过命令行运行```webpack```,在dist目录下就会生成bundle.js文件。到目前为止，我们到应用是相当无聊的，我是<a href="http://mithril.js.org/" target="_blank">Mithril.js</a>的忠实粉丝,因此我们通过<a href="http://mithril.js.org/" target="_blank">Mithril.js</a>来做一些东西，首先通过npm来安装这个库。

```
$ npm install --save mithril
```
现在打开```src/main.js```输入如下代码：
```javascript
var m = require('mithril');

var app = {
  view: function() {
    return m('div', 'hello world!')
  }
}

m.mount(document.getElementById('app'), app)
```
打开index.html,输入如下代码（请记得引入打包后的bundle.js文件）:
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Webpack Tutorial</title>
</head>
<body>
  <div id="app"></div>
  <script src="dist/bundle.js"></script>
</body>
</html>
```
接着通过命令行运行```webpack```生成新的包（bundle.js文件），现在在浏览器中打开index.html,你将看到```hello world!``` 。
如果你做到来这一步，那么恭喜你！你已经理解基本的webpack了。<br/>
让我们来稍微重构一下我们的app，我们来本地化我们的应用程序，这个要求我们把所有文本放在一个集中的地方，创建一个新的文件```src/resources.json```,这个文件里包含如下的JSON：
```json
{
  "en-US": {
    "HELLO_WORLD": "hello world!"
  }
}
```

回到```src/main.js```文件，通过json文件加载我们的信息（修改该文件为)：
```javascript
var m = require('mithril');
var resources = require('./resources.json')

var app = {
  view: function() {
    return m('div', resources['en-US'].HELLO_WORLD)
  }
}

m.mount(document.getElementById('app'), app)
```



