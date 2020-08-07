# New Features

tree shaking   


react hook

react fragment

real-time applications

{% embed url="https://socket.io" %}



## Context API

context is like a global value

use context.provider, then use this.context to get it

\`\`[`https://codesandbox.io/s/contextdemo-di5x7`](https://codesandbox.io/s/contextdemo-di5x7)\`\`

```text
React.createContext(defaultValue);
```

.When React renders a component that subscribes to this Context object it will read the current context value from the closest matching `Provider` above it in the tree.

#### `Context.Provider` <a id="contextprovider"></a>

```text
<MyContext.Provider value={/* some value */}>
```

#### `Context.Consumer` <a id="contextconsumer"></a>

```text
class MyClass extends React.Component {
  static contextType = MyContext;
  render() {
    let value = this.context;
    /* render something based on the value */
  }
}
```

