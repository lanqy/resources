## 一步一步教你创建react redux应用
Redux 已经成为构建React应用的标配，有大量的实例展示它是怎样做到的，但是react-Redux 应用有很多部分，例如：“Reducers”, “Actions”, “Action Creators”, “State”, “Middleware” 等等)，这些都具有颠覆性的。

当我开始学习它的时候，我找不到任何资料说明“构建react-Redux应用的时候，应该先构建哪个部分”或者一般怎样构建react－redux应用，因此我通过几个实例和文章来教你怎样一步步构建react－redux应用。
<br/>

注：我通过“模拟”以保持较高水平和不至于太杂乱。我将使用经典的<a href="https://github.com/reactjs/redux/tree/master/examples/todos">Todo list app</a>作为基础来创建任何react应用。如果你的应用有多个（screens）界面，只需要重复这个步骤到你到界面中即可。

###为什么要用Redux?

React—一个JS库，帮助我们将我们的应用拆分为多个组件，但是没有具体说明如何保持数据（state）的轨迹以及如何正常处理我们的所有事件（Actions）。

Redux—一个很受欢迎的库，为react提供一个可以轻松地保持数据（state）和事件（actions）。

> 实际上，Redux允许我们以我们的方式创建React应用，然后委托所有的状态（state）和事件（actions）到Redux上。
> 顺便说一个.一个简单到Todo应用，有八个步骤。理论上，早期的框架构建Todo应用很简单，但是做真实的应用比较难（这里指的是维护）。而React Redux做Todo应用就显得比较繁琐，但是真实的应用就比较方便（这里指的是维护）

让我们开始吧！

###第一步－写一个详细的模拟
这个模拟应该包含所有的数据和视觉效果（例如TodoItem的删除线，一个“All”的过滤器），
```
第一步：模拟每个界面，

怎样模拟：
＊ 1、越详细越好，
＊ 2、画出所有的数据和视觉效果（例如item删除线）。
```
如下图：

<img src="https://github.com/lanqy/blog/blob/master/1-RtA4NF2PI__vcarQgXEEBg.png" />

###把应用划分成为组件

尝试将应用划分为基于每个组件的用途的组件块。

我们有三个组件“AddTodo”, “TodoList” and “Filter”组件。
```
第二步：划分应用成为组件：
怎样划分：基于它们的用途来划分。
我们的应用有三个主要的“目的”：
1、添加一个新的Todo 项目（AddTodo组件）
2、展示Todo列表（TodoList组件）
3、过滤展示Todos（Filter组件）
```
如下图：

<img src="https://github.com/lanqy/blog/blob/master/1-AfzFa8zO_dQOmuSHL7bEww.png" />

###Redux术语：“Actions”和“States”
#####每个组件做这两件事情：
 1、根据一些数据渲染DOM，这些数据，我们称之为状态（state）。
 
 2、监听用户和事件并发送到一个JS方法，我们称之为操作（actions）。


