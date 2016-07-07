#React 生态系统入门第一部分（共三个部分）
* <a href="#user-content-update">更新</a>
* <a href="#user-content-introduction">介绍</a>
* <a href="#user-content-installment">这一期中</a>
* <a href="#user-content-prerequisite">先决条件</a>
* <a href="#user-content-code">代码</a>
* <a href="#user-content-description">项目描述</a>
* <a href="#user-content-creation">创建项目</a>
* <a href="#user-content-webpack">Webpack</a>
* <a href="#user-content-babel">Babel</a>
* <a href="#user-content-hot">模块热替换</a>
* <a href="#user-content-component">第一个React组件</a>
<h4 id="update">更新</h4>
<p>2016.07.06: 第一次发布</p>
<h4 id="introduction">介绍</h4>
<p>过去8个月，我一直在工作中使用React生态系统，我们创建应用来监控我们的交易状态，编辑我们的交易风险检查和控制我们的战略。</p>
<p>它证明了梦幻般的生态系统，鉴于其组合的性质和平易近人的学习曲线，React几乎已经成为提供一个消费级的企业级用户界面的有趣交付物。</p>
<p>我想通过一个入门的教程 分享我的学习经验，通过这个入门你将学习到：</p>
* 配置开发React应用的环境
* 创建React组件并让他们对数据变化做出反应
* 通过Redux管理应用的状态
<p>如果你是第一次接触React生态系统，我希望通过这个入门教程，你将很轻松的开始创建你的React应用</p>
<h4 id="installment">在这一期中</h4>
<p>在第一部分中，我们将会配置一个基本的React开发环境，在文章的末尾，你将拥有一个创建应用和动态重载的开发环境，当你的文件发生改变的时候，我们也会创建我们的的第一个React组件
</p>
<h4 id="installment">先决条件</h4>
<p>我假设你已经熟悉Node和NPM并且已经安装好这两个工具。你还应该熟悉(Javascript) ES6。你不需要是ES6专家，但是知道主要的新功能如箭头函数和解构赋值。</p>
<p>写这篇文章的时候，我使用的是Node6.2.0和NPM3.8.9版本</p>
<h4 id="code">代码</h4>
<p>你可以在这里找到第一部分的所有代码，每个部分将有自己的分支</p>
<h4 id="description">项目描述</h4>
<p>我们将要创建一个应用依托于Spotify的后台，我们的应用将允许用户：</p>
* 检索艺术家的专辑
* 检索给定专辑的曲目
* 播放曲目开头30秒

<p>以下是一个样本：</p>
<img src="mockup.png" />
<p>使用Spotify的后台，这样我们可以把更多的注意力集中放在前端开发上。</p>
