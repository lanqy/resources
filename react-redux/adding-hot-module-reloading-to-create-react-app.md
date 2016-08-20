###给create-react-app创建的项目，加上热加载功能

修改index.js文件

```js
import React from 'react';
import ReactDOM from 'react-dom';
import App from './App';
import './index.css';
const rootEl = document.getElementById('root');
ReactDOM.render(
  <App />,
  rootEl
);
if (module.hot) { //热替换代码
  module.hot.accept('./App', () => {
    const NextApp = require('./App').default;
    ReactDOM.render(
      <NextApp />,
      rootEl
    );
  }); 
}
```
