## 构建一个基于Redux的react应用
在这篇文章里，我们将深入理解以及学习为什么开发React应用的时候，使用Redux这么重要。我也将一步一步教你如何创建你的第一个Redux应用，包括怎样使用<a href="https://github.com/stormpath/stormpath-sdk-react"></a>于<a href="https://stormpath.com/product/authentication/">用户认证</a>。当你完成的时候，你将掌握这个知识并运用到你已有到React应用中。

###Redux是什么？

<a href="https://github.com/reactjs/redux">Redux</a>是一个用于帮助我们管理应用状态到的框架(library)。它的设计源于<a href="https://facebook.github.io/react/docs/flux-overview.html">Flux</a>,但是从编写Flux应用的痛苦中进化而来。如果你写过Flux应用，你将很快注意到Redux可以帮你自动做很多以前你需要手动做的事情，还有，你只有一个单一的状态容器，这是一个很大的优势，这样在你的应用中共享状态和重用代码会变得更加简单。

### Stores

store是一个简单的状态容器，这是存储你应用状态和actions调度和处理的地方。当你开始创建一个Redux应用时，你要想想你的应用程序的数据和状态应该如何存储。这是很重要的，因为Redux推荐一个应用只有一个store
