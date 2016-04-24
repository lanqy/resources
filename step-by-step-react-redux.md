## 一步一步教你创建react redux应用
Redux 已经成为构建React应用的标配，有大量的实例展示它是怎样做到的，但是react-Redux 应用有很多部分，例如：“Reducers”, “Actions”, “Action Creators”, “State”, “Middleware” 等等)，这些都具有颠覆性的。

当我开始学习它的时候，我找不到任何资料说明“构建react-Redux应用的时候，应该先构建哪个部分”或者一般怎样构建react－redux应用，因此我通过几个实例和文章来教你怎样一步步构建react－redux应用。
<br/>

注：我通过“模仿”已保持较高水平和不至于太杂乱。我将使用经典的<a href="https://github.com/reactjs/redux/tree/master/examples/todos">Todo list app</a>作为基础来创建任何react应用。如果你的应用有多个（screens）页面，只需要重复这个步骤到你到页面中即可。

###为什么要用Redux?

