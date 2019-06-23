---
description: Compare the most interested concept
---

# Compare

## React vs Angular

| React | Angular |
| :--- | :--- |
| library | framework |
| JSX | typescript |
| one direction data-flow | bi-direction data-flow |
| one way data binding | two way data binding |
| component based | MVC, component based |

## State vs Props

| State | Props |
| :--- | :--- |
| change status in component | pass data |
| setState\(\) | read-only \(setProps\(\) is deprecated\) |
| data structure that starts with a default value when a component mounts | component's configuration |
| may be mutated across time, mostly as a result of user events | don't have to be just data, can also be callback functions |

![](.gitbook/assets/image%20%2828%29.png)

## SQL vs No-SQL

| SQL | No-SQL |
| :--- | :--- |
| table based | key-value pairs, document-based, graph databases or wide-column stores |
| predefined schema | dynamic schema |
| use sql  | use unql |
| good fit for complex query | don't have standard interfaces |
| vertically scalable -----   increase the load on a single server | horizontally scalable  -------   adding more servers |
| ACID properties \(Atomicity, Consistency, Isolation and Durability\) | Brewers CAP theorem \(Consistency, Availability and Partition tolerance\). |

## Element vs Component

| Element | Component |
| :--- | :--- |
| the tag of an object representation of a DOM node | a function or a class which optionally accepts input and returns a React element |

## Component vs Pure Component

<table>
  <thead>
    <tr>
      <th style="text-align:left">Component</th>
      <th style="text-align:left">Pure Component</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p>implement shouldComponentUpdate() with shallow props and state comparison</p>
        <p>It&apos;s the simplest, fastest components we can write</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"></td>
      <td style="text-align:left">class App extends React.PureComponent {}</td>
    </tr>
    <tr>
      <td style="text-align:left"></td>
      <td style="text-align:left">PureComponent changed<code>shouldComponentUpdate, only rerender when state or props changes</code>
      </td>
    </tr>
  </tbody>
</table>| Stateless Component | Stateful Component |
| :--- | :--- |
| don't have state | have state |
| can use function expression to create | must use class expression |



![](.gitbook/assets/image%20%2821%29.png)

## Server Side Rendering vs Client Side Rendering

| Server Side Rendering | Client Side Rendering |
| :--- | :--- |
| SEO | low SEO |
| initial loading becomes faster | initial load might require more time, faster after initial load |
| good for static sites | good for web application |

## Null vs Undefined

| Null | Undefined |
| :--- | :--- |
| an assignment value | means a variable has been declared but has not yet been assigned a value |
| an object | a type itself |

## Call vs Apply

| Call | Apply |
| :--- | :--- |
| pass a single parameter | expect the second argument to be an array that it unpacks as arguments for the called function |
| call a function with a given value and arguments provided individually | call a function with a given value, and arguments provided as an array \(or an array-like object\) |

## Redux vs Flux

| Redux | Flex |
| :--- | :--- |
| one store | multiple store |
| multiple reducers | no reducer |
| implemented dispatch function | have to implement dispatch |
| library | pattern |
| implemented based on flux |  |

## Parameter vs Argument 

| Parameter  | Argument |
| :--- | :--- |
| a variable in a method definition | the data you pass into the method's parameters when a method is called |
| variable in the declaration of function | the actual value of this variable that gets passed to function |

## Presentational Component vs Container Component

## Component vs Container  

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Presentational Component</b>
      </th>
      <th style="text-align:left"><b>Container Component</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>dumb component</b>
      </td>
      <td style="text-align:left"><b>smart component</b>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Controlled Component </b>
      </td>
      <td style="text-align:left"><b>Uncontrolled ComponentSide</b>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Component</b>
      </td>
      <td style="text-align:left"><b>Container </b>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">no aware of redux</td>
      <td style="text-align:left">aware of redux</td>
    </tr>
    <tr>
      <td style="text-align:left">concerned with how things look</td>
      <td style="text-align:left">concerned with how things work</td>
    </tr>
    <tr>
      <td style="text-align:left">receive data and callbacks via props</td>
      <td style="text-align:left">provide the data and behavior to presentational or other container components</td>
    </tr>
    <tr>
      <td style="text-align:left">Change data: invoke call back from props</td>
      <td style="text-align:left">Change data: dispatch Redux action</td>
    </tr>
    <tr>
      <td style="text-align:left">read data from props</td>
      <td style="text-align:left">subscribe to Redux state</td>
    </tr>
    <tr>
      <td style="text-align:left">rarely have own state and do with UI state instead of data state</td>
      <td
      style="text-align:left">call flux actions and provide these as callbacks to the presentational
        components, often stateful</td>
    </tr>
    <tr>
      <td style="text-align:left">written by hand</td>
      <td style="text-align:left">generate by redux</td>
    </tr>
    <tr>
      <td style="text-align:left"><em>Accept props</em> to allow them to be dynamic and reusable. send the
        title of a button in props from the parent component to allow it to have
        a unique name.</td>
      <td style="text-align:left">focus on how things <em>work</em>.Smart components can fetch, capture changes
        and pass down application data.</td>
    </tr>
    <tr>
      <td style="text-align:left">takes its current value through <code>props</code> and notifies changes
        through callbacks like <code>onChange</code>
      </td>
      <td style="text-align:left">stores its own state internally</td>
    </tr>
    <tr>
      <td style="text-align:left">parent component &quot;controls&quot; it by handling the callback</td>
      <td
      style="text-align:left">query the DOM using a <code>ref</code> to find its current valu</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p></p>
        <p><em>Focus on the UI</em> Almost all basic UI components should be considered
          dumb components. Examples include loaders, modals, buttons, inputs, etc.</p>
      </td>
      <td style="text-align:left">
        <p></p>
        <p><em>Manipulates Data</em> Smart components can fetch, capture changes and
          pass down application data.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><em>Rarely include state</em>
      </td>
      <td style="text-align:left"><em>Manage state</em>
      </td>
    </tr>
  </tbody>
</table>Smart组件负责数据相关的应用逻辑，将获取到的数据通过props传递给Dumb组件，Dumb负责UI的呈现。

Smart usually as Dumb parents component

## Class Component vs Functional Component

| Class Component | Functional Component |
| :--- | :--- |
| allow you to use additional features like local state and lifecycle hooks | receive props and renders them to the page, can use pure function |
| to enable your component to have direct access to your store and thus holds state | also called stateless, dumb or presentational components |

## setState\(\) vs forceUpdated\(\)

| setState\(\) | forceUpdated\(\) |
| :--- | :--- |
| used to update the component state with one or more new state properties | a way to force re-render of the component and its children |
| a way of mutating the state and managing view updates | doesn't mutate the state at all |

## XML vs JSON

| XML | JSON |
| :--- | :--- |
| surrounded with HTML tags | an Object |
| slower | faster |

