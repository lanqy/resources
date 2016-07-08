#React 生态系统入门第一部分（共三个部分）

- <a href="#user-content-update">更新</a>
- <a href="#user-content-introduction">介绍</a>
- <a href="#user-content-installment">这一期中</a>
- <a href="#user-content-prerequisite">先决条件</a>
- <a href="#user-content-code">代码</a>
- <a href="#user-content-description">项目描述</a>
- <a href="#user-content-creation">创建项目</a>
- <a href="#user-content-webpack">Webpack</a>
- <a href="#user-content-babel">Babel</a>
- <a href="#user-content-hot">模块热替换</a>
- <a href="#user-content-component">第一个React组件</a>

<h4 id="update">更新</h4>
<p>2016.07.06: 第一次发布</p>
<h4 id="introduction">介绍</h4>
<p>过去8个月，我一直在工作中使用React生态系统，我们创建应用来监控我们的交易状态，编辑我们的交易风险检查和控制我们的战略。</p>
<p>它证明了梦幻般的生态系统，鉴于其组合的性质和平易近人的学习曲线，React几乎已经成为提供一个消费级的企业级用户界面的有趣交付物。</p>
<p>我想通过一个入门的教程 分享我的学习经验，通过这个入门你将学习到：</p>

- 配置开发React应用的环境 
- 创建React组件并让他们对数据变化做出反应
- 通过Redux管理应用的状态

<p>如果你是第一次接触React生态系统，我希望通过这个入门教程，你将很轻松的开始创建你的React应用</p>
<h4 id="installment">在这一期中</h4>
<p>在第一部分中，我们将会配置一个基本的React开发环境，在文章的末尾，你将拥有一个创建应用和动态重载的开发环境，当你的文件发生改变的时候，我们也会创建我们的的第一个React组件
</p>
<h4 id="prerequisite">先决条件</h4>
<p>我假设你已经熟悉Node和NPM并且已经安装好这两个工具。你还应该熟悉(Javascript)ES6。你不需要是ES6专家，但是知道主要的新功能如箭头函数和解构赋值。</p>
<p>写这篇文章的时候，我使用的是Node6.2.0和NPM3.8.9版本</p>
<h4 id="code">代码</h4>
<p>你可以在这里找到第一部分的所有代码，每个部分将有自己的分支</p>
<h4 id="description">项目描述</h4>
<p>我们将要创建一个应用依托于Spotify的后台，我们的应用将允许用户：</p>

- 检索艺术家的专辑
- 检索给定专辑的曲目
- 播放曲目开头30秒

<p>以下是一个样本：</p>
<img src="mockup.png" />
<p>使用Spotify的后台，这样我们可以把更多的注意力集中放在前端开发上。</p>

<h4 id="creation">创建项目</h4>
<p>让我们开始创建我们的项目</p>
```js
mkdir respotify
cd respotify
npm init -y
```
<p>这个将在我们的根目录下创建一个package.json文件</p>
<p>下一步，在根目录下创建一个src目录,在src目录中创建一个index.html文件：</p>
```html
<!DOCTYPE html>
<html>
  <head>
    <title>Respotify</title>
  </head>
  <body>
    <h1>Respotify</h1>
    <div id="container"></div>
    <script src="/bundle.js"></script>
  </body>
</html>
```
<p>index.html是我们应用的入口，其中有两行代码比较有趣:</p>
```html
 <div id="container"></div>
  <script src="/bundle.js"></script>
```
<p>我们的React组件将渲染到id为container的div中，这个将会更加清晰，通过这个编文章</p>
<p>构建的时候，我们要放在一起将所有的JS文件合并成一个文件bundle.js，并且在index.html引用它</p>
<p>下一步，创建index.js：</p>
```js
console.log("Hello,world!");
```
<p>index.js是我们的应用程序的主要的Javascript文件，现在，我们仅仅打印一些日志，以确保我们的构建正常工作。</p>

这个时候，我们的目录结构应该像这样：
```js
respotify
 -src
  --index.html
  --index.js
 --package.json
```

<h4 id="webpack">Webpack</h4>
<p>现在好了，我们将从头开始组建我们的构建环境，你可能听说过很多开发样本，例如<a href="https://github.com/kriasoft/react-starter-kit">这里</a>提供了完整的开发配置环境，虽然这个很有用，但是我觉得至少自己会创建基本的配置，这样你才知道主要的东西是如何工作的</p>
<p>我们从<a href="https://webpack.github.io/">Webpack</a>开始构建我们的环境，简单地说，Webpack为我们打包静态资源，虽然有很多不同类型的打包工具，但是Webpack提供的一些功能，获得React社区的青睐，我们只是使用其中的一部分。</p>
<p>让我们开始安装Webpack：</p>
```js
npm install webpack --save-dev
```
<p>一旦安装完整，检查package.json文件Webpack是否在你的dev依赖。</p>
<p>我们使用Webpack做两件事：</p>
- 获取我们的应用程序代码，并从代码中生成静态资源
- 启动一个开发服务器来服务静态资源

<p>因为Webpack是配置驱动的，我们就从这里开始，在根目录下创建一个webpack.config.js文件：</p>
```js
const webpack = require('webpack'); // line 1
const path = require('path');// line 2
 // line 3
const PATHS = { // line 4
  app: './src/index.js', // line 5
  dist: path.join(__dirname, 'dist') // line 6
}; // line 7
 // line 8
module.exports = { // line 9
  entry: { // line 10
    javascript: PATHS.app // line 11
  }, // line 12
  output: { // line 13
    path: PATHS.dist, // line 14
    publicPath: '/', // line 15
    filename: 'bundle.js' // line 16
  }, // line 17
  devServer: { // line 18
    contentBase: PATHS.dist // line 19
  } // line 20
}; // line 21
```
<p>让我们继续</p>
<p>在webpack.config.js文件顶部，我们引用webpack和path模块，然后为我们的应用程序定义几个常量</p>
<p>[第9行] 这个是我们Webpack配置的开始</p>
<p>[第10行] 这里最终成为我们bundle.js文件的<a href="https://webpack.github.io/docs/configuration.html#entry">入口</a>，在这个例子中，我们有一个单独的JS文件（index.js）服务，做为我们的入口文件，Webpack将构建index.js以及任何其他JS文件在index.js中声明依赖的，与依赖那些依赖等，最终合成一个单一的bundle.js文件。想象一下一个依赖折叠成一个节点的图形。</p>
<p>[第13行] <a href="https://webpack.github.io/docs/configuration.html#output">这里</a>是我们设置的配置文件。在这个例子中，我们告诉Webpack：</p>
- 输出其编译结果到dist目录下
- 将输出的文件的网址设置为首页路径
- 调用其编译的bundle.js结果

<p>[第18行] 这里我们制定Webpack服务器从dist目录下请求静态资源目录。</p>
<p>现在尝试在您的终端运行此命令（确保您在您的项目的根目录和节点在您的路径下）：</p>
```js
node node_modules/webpack/bin/webpack.js
```
link: http://patternhatch.com/2016/07/06/a-primer-on-the-react-ecosystem-part-1-of-3/

