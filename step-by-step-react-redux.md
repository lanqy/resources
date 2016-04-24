## 一步一步教你创建react redux应用
Redux 已经成为构建React应用的标配，有大量的实例展示它是怎样做到的，但是react-Redux 应用有很多部分，例如：“Reducers”, “Actions”, “Action Creators”, “State”, “Middleware” 等等)，这些都具有颠覆性的。

当我开始学习它的时候，我找不到任何资料说明“构建react-Redux应用的时候，应该先构建哪个部分”或者一般怎样构建react－redux应用，因此我通过几个实例和文章来教你怎样一步步构建react－redux应用。
<br/>

注：我通过“模仿”已保持较高水平和不至于太杂乱。我将使用经典的<a href="https://github.com/reactjs/redux/tree/master/examples/todos">Todo list app</a>作为基础来创建任何react应用。如果你的应用有多个（screens）页面，只需要重复这个步骤到你到页面中即可。

###为什么要用Redux?

React—一个JS库，帮助我们将我们的应用拆分为多个组件，但是没有具体说明如何保持数据（state）的轨迹以及如何正常处理我们的所有事件（Actions）。

Redux—一个很受欢迎的库，为react提供一个可以轻松地保持数据（state）和事件（actions）。

> 实际上，Redux允许我们以我们的方式创建React应用，然后委托所有的状态（state）和事件（actions）到Redux上。
> 顺便说一个.一个简单到Todo应用，有八个步骤。理论上，早期的框架构建Todo应用很简单，但是做真实的应用比较难（这里指的是维护）。而React Redux做Todo应用就显得比较繁琐，但是真实的应用就比较方便（这里指的是维护）

让我们开始吧！

