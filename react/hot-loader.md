# Hot Loader

`Hot Loader is a plugin for webpack that allows instantaneous live refresh without losing state while editing react components`



[`@hot-loader/react-dom`](https://github.com/hot-loader/react-dom) replaces the "react-dom" package of the same version, but with additional patches to support hot reloading.



Webpack Hot-Module-Replacement  HMR

![](../.gitbook/assets/image%20%2870%29.png)

![](../.gitbook/assets/image%20%2873%29.png)

For react

HMR use root component



```text
import React from 'react';
import ReactDOM from 'react-dom';
import App from './App';'

import './index.css';

const rootEl = document.getElementById("root");

ReactDOM.render(
    <App />,
    rootEl
);

if(module.hot) {
    // while APP is updated or independent is updated，reenter and rerender
    module.hot.accept("./App", () => {
        const App = require("./App").default;
    
        ReactDOM.render(
            <App />,
            rootEl
        );
    });
}

render();



Hot Loader 2

class Counter extends Component {

  constructor(props) {

    super(props)

    this.state = { counter: 0 }

    this.handleClick = this.handleClick.bind(this)

  }

  handleClick() {

    this.setState({

      counter: this.state.counter + 1

    })

  }

  render() {

    return (

      <div className={this.props.sheet.container} onClick={this.handleClick}>

        {this.state.counter}

      </div>

    )

  }

}


const styles = {

  container: { 

    backgroundColor: 'yellow'

  }

}


const __exports_default = useSheet(styles)(Counter)

export default __exports_default



register('Counter.js#Counter', Counter)

register('Counter.js#exports#default', __exports_default) // every export too


3 

import createProxy from 'react-proxy'


let proxies = {}

const UNIQUE_ID_KEY = '__uniqueId'


export function register(uniqueId, type) {

  Object.defineProperty(type, UNIQUE_ID_KEY, {

    value: uniqueId,

    enumerable: false,

    configurable: false

  })


  let proxy = proxies[uniqueId]

  if (proxy) {

    proxy.update(type)

  } else {

    proxy = proxies[id] = createProxy(type)

  }

}


// Resolve 发生在 element 被创建的时候，而不是声明的时候

const realCreateElement = React.createElement

React.createElement = function createElement(type, ...args)  {

  if (type[UNIQUE_ID_KEY]) {

    type = proxies[type[UNIQUE_ID_KEY]].get()

  }


  return realCreateElement(type, ...args)

}
```





## Uses

```text
npm install --save-dev react-hot-loader

{
  "plugins": ["react-hot-loader/babel"]
}
```

Mark your root component as _hot-exported_:

```text

import { hot } from 'react-hot-loader/root';
const App = () => <div>Hello World!</div>;
export default hot(App);
```

Make sure `react-hot-loader` is required before `react` and `react-dom`

`OR .  import 'react-hot-loader'` in your main file

 OR . prepend your webpack entry point with `react-hot-loader/patch`, for example:

```text
// webpack.config.js
module.exports = {
  entry: ['react-hot-loader/patch', './src'],
  // ...
};
```

[`@hot-loader/react-dom`](https://github.com/gaearon/react-hot-loader#hot-loaderreact-dom)



```text
 useState(initialState); // will never updated (preserve state)
❄️ useEffect(effect); // no need to update, updated on every render
❄️ useEffect(effect, []); // "on mount" hook. "Not changing the past"
🔥 useEffect(effect, [anyDep]); // would be updated

🔥 useEffect(effect, ["hot"]); // the simplest way to make hook reloadable
```

