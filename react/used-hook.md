# Hook

## useState

useState\(\) returns an array with exactly two elements: 

\(1\) Your current state value, \(2\) A method to update your state value.

useState\(\) will replace the old state instead of merging. 

```jsx
import React, { useState } from "react";
import Person from "./Person/Person";

const App = props => {
    const [personState, setPersonState] = useState({
        person: [
            { name: "Harry", age: 24 }
        ]
    });
    
    const [otherState, setOtherState] = useState("some other value");
    
    const switchNameHandler = () => {
        setPersonState({
            person: [
                {name: "Harry Lu", age: 25}
            ]
        });
    };
    
    return (
        <div className="App">
            <button onClick={switchNameHandler}>Switch Name</button>
            <Person
                name={personState.person[0].name}
                age={personState.person[0].age}
            /> 
        </div>
    );
}

export default App;
```

## useEffect & useRef & useContext

useEffect:  `componentDidMount ·  componentDidUpdate`  `componentWillUnmount`

```jsx
import React, { useEffect, useRef, useContext } from 'react';
import AuthContext from '../../context/auth-context';

const cockpit = props => {
  const toggleBtnRef = useRef(null);
  const authContext = useContext(AuthContext);

  useEffect(() => {
    // Http request...
    // same as componentDidMount and componentDidUpdate
    // setTimeout(() => {
    //   alert('Saved data to cloud!');
    // }, 1000);
    toggleBtnRef.current.click();
    return () => {
      // clean-up code here
      // same as componentWillUnmount 
    };
  }, []); // only re-run the effect if the value inside changes

  return (
    <div>
      <button ref={toggleBtnRef}>
        Toggle Persons
      </button>
      <button onClick={authContext.login}>Log in</button>
    </div>
  );
};

export default React.memo(cockpit);
```

## UseContext

recieved a React.createContext

return   ---- `<MyContext.Provider>`   `value` prop  

```text
const value = useContext(MyContext);
```

## Counter Example

```jsx
import React, { useState } from "react";

const App = (props) => {

  const [counter, setCounter] = useState(0);

  return (
    <React.Fragment>
      <span>You Clicked {counter} times!</span>
      <button onClick={() => setCounter(counter + 1)}>Increase</button>
      <button onClick={() => setCounter(counter - 1)}>Decrease</button>
    </React.Fragment>
  );
}

export default App;
```

## React Counter using Hooks

```jsx
import React, { useState, useEffect } from "react";
import ReactDOM from "react-dom";

function App() {
  const [num, setNum] = useState(Number(localStorage.getItem("num")) || 0);

  useEffect(() => {
    localStorage.setItem("num", num);
  }, [num]);

  return (
    <div>
      {num}
      <button onClick={() => setNum(num + 1)}>Add</button>
      <button onClick={() => setNum(num - 1)}>Subtract</button>
    </div>
  );
}

ReactDOM.render(<App />, document.getElementById("root"));
```

## Using the Effect Hook



```text
import React, { useState, useEffect } from 'react';

function FriendStatus(props) {
  const [isOnline, setIsOnline] = useState(null);

  useEffect(() => {
    function handleStatusChange(status) {
      setIsOnline(status.isOnline);
    }
    ChatAPI.subscribeToFriendStatus(props.friend.id, handleStatusChange);
    // Specify how to clean up after this effect:
    return function cleanup() {
      ChatAPI.unsubscribeFromFriendStatus(props.friend.id, handleStatusChange);
    };
  });

  if (isOnline === null) {
    return 'Loading...';
  }
  return isOnline ? 'Online' : 'Offline';
```

`useEffect` lets us express different kinds of side effects after a component renders. Some effects might require cleanup so they return a function

```text
  useEffect(() => {
    function handleStatusChange(status) {
      setIsOnline(status.isOnline);
    }

    ChatAPI.subscribeToFriendStatus(props.friend.id, handleStatusChange);
    return () => {
      ChatAPI.unsubscribeFromFriendStatus(props.friend.id, handleStatusChange);
    };
  });
```

#### Use Multiple Effects to Separate Concerns <a id="tip-use-multiple-effects-to-separate-concerns"></a>

 [you can use the _State_ Hook more than once](https://reactjs.org/docs/hooks-state.html#tip-using-multiple-state-variables), you can also use several effects. This lets us separate unrelated logic into different effects:





### Custom Hook <a id="extracting-a-custom-hook"></a>

**A custom Hook is a JavaScript function whose name starts with ”`use`” and that may call other Hooks.**

```text
import { useState, useEffect } from 'react';

function useFriendStatus(friendID) {  const [isOnline, setIsOnline] = useState(null);

  useEffect(() => {
    function handleStatusChange(status) {
      setIsOnline(status.isOnline);
    }

    ChatAPI.subscribeToFriendStatus(friendID, handleStatusChange);
    return () => {
      ChatAPI.unsubscribeFromFriendStatus(friendID, handleStatusChange);
    };
  });

  return isOnline;
}
```



```text
function FriendStatus(props) {
  const isOnline = useFriendStatus(props.friend.id);
  if (isOnline === null) {
    return 'Loading...';
  }
  return isOnline ? 'Online' : 'Offline';
}


function FriendListItem(props) {
  const isOnline = useFriendStatus(props.friend.id);

  return (
    <li style={{ color: isOnline ? 'green' : 'black' }}>
      {props.friend.name}
    </li>
  );
}
```

