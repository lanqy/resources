## 构建一个基于Redux的react应用
在这篇文章里，我们将深入理解以及学习为什么开发React应用的时候，使用Redux这么重要。我也将一步一步教你如何创建你的第一个Redux应用，包括怎样使用<a href="https://github.com/stormpath/stormpath-sdk-react">Stormpath React SDK </a>于<a href="https://stormpath.com/product/authentication/"> user authentication（用户认证）</a>。当你完成的时候，你将掌握这个知识并运用到你已有到React应用中。

###Redux是什么？

<a href="https://github.com/reactjs/redux">Redux</a>是一个用于帮助我们管理应用状态到的框架(library)。它的设计源于<a href="https://facebook.github.io/react/docs/flux-overview.html">Flux</a>,但是从编写Flux应用的痛苦中进化而来。如果你写过Flux应用，你将很快注意到Redux可以帮你自动做很多以前你需要手动做的事情，还有，你只有一个单一的状态容器，这是一个很大的优势，这样在你的应用中共享状态和重用代码会变得更加简单。

### Stores

store是一个简单的状态容器，这是存储你应用状态和actions调度和处理的地方。当你开始创建一个Redux应用时，你要想想你的应用程序的数据和状态应该如何存储。这是很重要的，因为Redux推荐一个应用只有一个store，而且由于状态是共享的，因此在开始创建应用的时候，想好这些尤为重要。

### Actions

Actions 是一些用于描述我们怎样改变我们应用状态的对象，你可以这么认为actions就是我们状态树的API。例如，一个添加用户的action可以像这样：

```javascript
{
  type: 'ADD_USER',
  data: {
    name: 'Foo',
    email: 'foo@bar.com',
    password: 'Foobar123_'
  }
}
```
为了让代码更清晰，更易于重用,通常是使用一个生成器(方法)生成操作对象，即，上面的例子，我们可以创建一个类似于```addUser(name, email, password) ```的函数来生成对象。如你所见，actions本身什么都不做，一个action仅仅是一个用于描述我们怎样改变我们应用状态的对象。

### Reducers

Actions很酷，但是它们并没有太大的意义。这就是reducers存在的意义。
Reducers是action处理器，用于在store中调度actions以及在状态变化中简化actions操作。如果我们要在store中调度action（ADD_USER）,我们将拥有一个reducer调用action(ADD_USER)并添加一个新的用户到我们到应用状态中。
### 创建Redux应用
现在，当你了解的基础知识以后，让我们继续创建我们第一个基于Redux的应用程序。<br/>
为了让事情变得简单，我们将要创建一个todo应用程序，这样我们可以玩转很多Redux的重要概念，而不用过多的关注应用本身。<br/>
我们考虑一下一个todo应用程序，需要些什么基本的东西。首先一个todo程序，由一个列表组成。其实这个列表包含一些我们可以改变的项目。
从应用的状态来看，我们可以这样定义我们的模型（model）：
```javascript
{
  todo: {
    items: [
      {
        message: "Finish Redux blog post...",
        completed: false
      }
    ]
  }
}
```
### 添加 Actions

我们要怎样处理我们应用的状态呢？首先，我们添加一个新待办项目到我们状态中去，让我们创建一个action来做这件事：
```javascript
function addTodo(message) {
  return {
    type: 'ADD_TODO',
    message: message,
    completed: false
  };
}
```
注意```type```这个字段，这个必须是唯一的，用于表明action的意图。
type字段的约定格式为大写字母，并且每个单词以下划线作为分隔，接下来你将使用这个名字／标示符在你的reducers中来处理具体的actions，并把它们变成可变的状态。
一旦我们增加了我们的待办事项，我们肯定希望能够将其标记为已完成状态，我们也可以删除它，可以清空所有的待办项目。
因此让我们创建actions来做这些事情：
```javascript
function completeTodo(index) {
  return {
    type: 'COMPLETE_TODO',
    index: index
  };
}

function deleteTodo(index) {
  return {
    type: 'DELETE_TODO',
    index: index
  };
}

function clearTodo() {
  return {
    type: 'CLEAR_TODO'
  };
}
```
到目前为止，我们已经定义好我们的actions，让我们继续定义我们的store，如前所述，store是Redux应用的核心，所有的状态(state)、调度器(dispatched actions)、reducers都依赖于它。
```javascript
import { createStore } from 'redux';

var defaultState = {
  todo: {
    items: []
  }
};

function todoApp(state, action) {
}

var store = redux.createStore(todoApp, defaultState);
```
### 添加Reducers
现在，我们已经拥有一些actions和一个store。让我们创建我们的第一个reducer，如前所述，reducer仅仅是一个action处理器，拥有处理actions和改变应用的状态（state）。
让我们先处理我们的```ADD_TODO``` action，如下所示：
```javascript
function todoApp(state, action) {
  switch (action.type) {
    case 'ADD_TODO':
      var newState = Object.assign({}, state);

      newState.todo.items.push({
        message: action.message,
        completed: false
      });

      return newState;

    default:
      return state;
  }
}
```
注意，当我们说一个reducer“改变”了应用的状态，如果一个状态需要改变，我们真正要做的是创建一个状态（state）的副本，并修改这个状态的副本。如果状态没有改变,那我们就返回相同的状态。任何情况下，如果你直接修改原始的状态（state），这意味着你将改变状态的历史。
现在我们有了第一个我们的action处理器，让我们添加其它的：
```javascript
function todoApp(state, action) {
  switch (action.type) {
    case 'ADD_TODO':
      var newState = Object.assign({}, state);

      newState.todo.items.push({
        message: action.message,
        completed: false
      });

      return newState;

    case 'COMPLETE_TODO':
      var newState = Object.assign({}, state);

      newState.todo.items[action.index].completed = true;

      return newState;

    case 'DELETE_TODO':
      var items = [].concat(state.todo.items);

      items.splice(action.index, 1);

      return Object.assign({}, state, {
        todo: {
          items: items
        }
      });

    case 'CLEAR_TODO':
      return Object.assign({}, state, {
        todo: {
          items: []
        }
      });

    default:
      return state;
  }
}
```

https://stormpath.com/blog/build-a-redux-powered-react-application/
