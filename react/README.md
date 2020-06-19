# React

## React

React is a Javascript library for building User Interfaces.

## How does React work

React creates a virtual DOM. When state changes in a component it firstly runs a "diffing" algorithm, which identifies what has changed in the virtual DOM. The second step is reconciliation, where it updates the DOM with the results of diff.

## How Virtual DOM works

React builds up its own "virtual DOM" which is a lightweight representation of the DOM optimized for React's diffing algorithms and reconciliation process. Virtual DOM changes eventually propagate to the actual DOM at the end of the reconciliation process.

## React Advantages

* It's easy to know how a component is rendered, you just need to look at the render function.
* JSX makes it easy to read the code of your components. It's also really easy to see the layout, or how components are plugged/combined with each other.
* You can render React on the server-side. This enables improves SEO and performance. 
* It's easy to test.
* You can use React with any framework \(Backbone.js, Angular.js\) as it's only a view layer. 



## React - Redux Workflow



## Toolchains -  contains package manager, bundler and compiler

* Create React App - single-page application
* NextJS - static and server-rendered applications including styling and routing solutions
* Gatsby - static websites 

## Redux vs setState\(\)

Use Redux if your state is shared across multiple components. 

Use setState\(\) if it’s used only in a single component.

## Using State Correctly

* Do not modify state directly
* State updates may be asynchronous
* State updates are merges

## Elements vs Components

React elements are the building blocks of React applications. An element describes what you want to see on the screen. React elements are immutable. Typically, elements are not used directly, but get returned from components. 

React components are small, reusable pieces of code that return a React element to be rendered to the page. The simplest version of React component is a plain JavaScript function that returns a React element. 

## React Router

React Router is the standard routing library for React. React Router keeps your UI in sync with the URL. It has a simple API with powerful features like lazy code loading, dynamic route matching, and location transition handling. 



```text
import { BrowserRouter, Route, Link } from "react-router-dom";
APP: <Switch>
  <Route exact path="/" component={Home} />
  <Route path="/about" component={About} />
  <Route path="/contact" component={Contact} />
</Switch>

import { BrowserRouter } from "react-router-dom";
ReactDOM.render(
  <BrowserRouter>
    <App />
  </BrowserRouter>,
  holder
);

```

## pass props in the router.

use render.

```text
<Route
  path='/dashboard'
  render={(props) => (
    <Dashboard {...props} isAuthed={true} />
  )}
/>
```

## Synthetic Event

Synthetic Event is a cross-browser wrapper around the browser's native event. It has the same interface as the browser's native event, including `stopPropagation()` and `preventDefault()`, except the events work identically across all browsers. 

## JSX

JSX is a syntax extension to JavaScript. It is similar to a template language, but it has full power of JavaScript. JSX gets compiled to `React.createElement()` calls which return plain JavaScript objects called “React elements”.

## Why JSX

React embraces the fact that rendering logic is inherently coupled with other UI logic: how events are handled, how the state changes over time, and how the data is prepared for display. Instead of artificially separating technologies by putting markup and logic in separate files, React separates concerns with loosely coupled units called "components" that contain both. 

## Understanding JSX

```javascript
// JSX
return (
    <div className="App"> 
        <h1>React</h1>
    </div>
);

// JavaScript
return React.createElement("div", {className: "App"}, 
    React.createElement("h1", null, "React"));
```

## One way data flow in React vs Two way data binding in Angular

In Angular, if you change the UI element, then the corresponding model state changes as well. Additionally, if you change the model state, then the UI element changes.

In React, when the model state update, it will render the change in the UI element. However, if you change the UI element, the model state does not change. Any state is always owned by some specific component, and any data or UI derived from that state can only affect components below them in the tree. 

## Two Kinds of Applications 

| Single Page Applications | Multi Page Applications |
| :--- | :--- |
| Only ONE HTML Page, Content is \(re\)rendered on Client | Multiple HTML Pages, Content is rendered on Server. |
| Typically only ONE ReactDOM.render\(\) call | One ReactDOM.render\(\) call per "widget" |

## Server-Side Rendering - pros & cons 

advantages:

* search engines can crawl the site for better SEO
* initial loading becomes faster
* great for static sites

disadvantages:

* frequent server requests
* full page reloads, overall slow page rendering
* non-rich site interactions

## Client-Side Rendering - pros & cons

advantages:

* rich site interactions
* fast website rendering after the initial load
* great for web applications
* robust selection of JavaScript libraries

disadvantages:

* low SEO if not implemented correctly
* initial load might require more time
* in most cases, requires an external library

## PureComponent

`React.PureComponent`is similar to `React.Component`. The difference between them is that `React.Component` doesn't implement `shouldComponentUpdate()`, but `React.PureComponent` implements it with a shallow prop and state comparison. 

## React.memo

`React.memo` is a higher order component. It's similar to `React.PureComponent` but for function components instead of classes. 

If your function component renders the same result given the same props, you can wrap it in a call to `React.memo` for a performance boost in some cases by memoizing the result. This means that React will skip rendering the component, and reuse the last rendered result. 

By default it will only shallowly compare complex objects in the props object. If you want control over the comparison, you can also provide a custom comparison function as the second argument. 

This method only exists as a performance optimization. 

## React.Fragment

The `React.Fragment` component lets you return multiple elements in a `render()` method without creating an additional DOM element. You can also use it with the shorthand `<></>`syntax. 

## React.lazy

`React.lazy()` lets you define a component that is loaded dynamically. This helps reduce the bundle size to delay loading components that aren't used during the initial render. 

[React.lazy & Suspense Code Sample]()

## Suspense

The suspense component shows the fallback content while you are waiting for the child components to load when the parent component renders. 

## Why need super\(props\)

If you don't initialize state and you don't bind methods, you don't need to implement the constructor for your React component.

The constructor for a React component is called before it is mounted. When implementing the constructor for a React.component subclass, you should call super\(props\) before any other statement. Otherwise, `this.props` will be undefined in the constructor, which can lead to bugs. 

## How to re-render out of Lifecycle

this.forceUpdate\(\)

## User Authentication Login

The React App sends the Auth to the server, and then the server sends back a Token that will be stored in the JavaScript localStorage. After that we can use the Token we received to request for protected resources from the server.

## 3 ways for Debugging React Apps

* Finding Logical Errors by using Chrome Developer Tools - Check your code inside Source
* Working with the React Developer Tools Chrome Extension 
* Using Error Boundaries \(**only use Error Boundaries for cases where you know that it might fail and you can't control that\)** 

## Error Handling Method - Error Boundary

Error boundaries are React components that catch JavaScript errors anywhere in their child component tree, log those errors, and display a fallback UI instead of the component tree that crashed. Error boundaries catch errors during rendering, in lifecycle methods, and in constructors of the whole tree below them.

A class component becomes an error boundary if it defines either \(or both\) of the lifecycle methods `static getDerivedStateFromError()` or `componentDidCatch()`. Use `static getDerivedStateFromError()` to render a fallback UI after an error has been thrown. Use `componentDidCatch()` to log error information. 

Error Boundary does not catch errors for:

* Event handlers
* Asynchronous code
* Server side rendering
* Errors thrown in the error boundary itself

Errors that were not caught by any error boundary will result in unmounting of the whole React component tree.

[**ErrorBoundary Sample Code**]()\*\*\*\*

## Composition vs inheritance in React

React has a powerful composition model, and composition is recommended instead of inheritance to reuse code between components. 

## Rendering Multiple Components

* You can build collections of elements and include them in JSX using curly braces {}.
* Using `<React.Fragment />`
* Return an array of elements using Map function and assign key to them 

## Keys

A "key" is a special string attribute you need to include when creating arrays of elements. Keys help React identify which items have changed, are added, or are removed. Keys should be given to the elements inside an array to give the elements a stable identity. 

## Where in a React component should you make an AJAX request?

componentDidMount

## Controlled Component vs Uncontrolled Component

An input form element whose value is controlled by React is called a controlled component. When a user enters data into a controlled component a change event handler is triggered and your code decides whether the input is valid \(by re-rendering with the updated value\). If you do not re-render then the form element will remain unchanged. 

An uncontrolled component works like form elements do outside of React. When a user inputs data into a form field \(an input box, dropdown, etc\) the updated information is reflected without React needing to do anything. However, this also means that you can't force the field to have a certain value.

In most cases you should use controlled components. 

[Controlled Components Code Sample]()

## Single-page Application

A single-page application is an application that loads a single HTML page and all the necessary assets \(such as JavaScript and CSS\) required for the application to run. Any interactions with the page or subsequent pages do not require a round trip to the server which means the page is not reloaded.

![](../.gitbook/assets/image%20%2850%29.png)

we write our code in such a way that it can run on both the server and in a browser, meaning we only render once on the server and subsequent pages are fetched without full page reloads.

To facilitate this we use NodeJS to serve our front-end application. This is a small layer which sits between our back-end and the client. It does API calls to fetch all the data it needs to render the current view and then returns the full markup back to the browser.

One thing to note is that these API calls are going from server to server over a high-speed internet connection meaning we don’t have to burden our users with doing these calls over \(much\) slower connections.

## Refs

React supports a special attribute that you can attach to any component. The ref attribute can be an object created by `React.createRef()`function or a callback function. When the ref attribute is a callback function, the function receives the underlying DOM element or class instance as its argument. This allows you to have direct access to the DOM element or component instance. 

## Refs vs document.getElementsById\(\)

By using Refs, you can create reusable component as much as you want. 

## Forwarding Refs

Ref forwarding is a technique for automatically passing a ref through a component to one of its children. This is typically not necessary for most components in the application. However, it can be useful for some kinds of components, especially in reusable component libraries. 

## Portals

Portals provide a first-class way to render children into a DOM node that exists outside the DOM hierarchy of the parent component.

A typical use case for portals is when a parent component has an `overflow: hidden` or `z-index` style, but you need the child to visually " break out" of its container. 

## Higher Order Component

A higher order component is a function that takes a component and returns a new component. HOC allows you to reuse code, logic and bootstrap abstraction.The most common is probably Redux's connect function. Beyond simply sharing utility libraries and simple composition, HOC is the best way to share behavior between React components. If you find yourself writing a lot of code in different places that does the same thing, you may be able to refactor that code into a reusable HOC.

[Higher Order Component Sample Code]()

[https://levelup.gitconnected.com/understanding-react-higher-order-components-by-example-95e8c47c8006](https://levelup.gitconnected.com/understanding-react-higher-order-components-by-example-95e8c47c8006)

## Why is it advised to pass a callback function to setState as opposed to an Object

Since this.props and this.state may be updated asynchronously, you should not rely on their values for calculating the next state.

## How would you prevent a component from rendering

* return null in the render method function
* return false in shouldComponentUpdate\(\) lifecycle method function in class based component

## Conditional Rendering

* if else statement
* true && expression
* condition ? true : false

## How to access the underlying DOM component

When the ref attribute is used on an HTML element, the ref created in the constructor with React.createRef\(\) receives the underlying DOM element as its current property. 

## Why would you eject from create-react-app

Until you eject you are unable to configure web-pack or babel presets.

## Props vs State

`Props` are inputs to a React component. They are data passed down from a parent component to a child component. Props are read only. 

`State` is an internal object for a particular react component and can change, as it determines the state of the component. It's not visible to other components.  

`props.children` contains the content between the opening and closing tags of a component.

only changes in `props` and/or `state` trigger React to re-render the components and potentially update the DOM in the browser. 

## Pure Component

shouldComponentUpdate

## Pure Functional Component 

A component that has no internal state of its own, nor any side effects, and thus is often written as a function as opposed to an ES6 class. 

## Why need render method

To determine what should be rendered for a particular component. Could be a complex nested object of other child React components, or it could be as simple as a primitive JavaScript object. 

## PropTypes

They help indicate to React what data types a React component's properties are and should accept. 

[PropTypes Sample Code]()

## Optimizing Performance

* Use the Production Build
* Profiling Components with the Chrome Performance Tab
* Profiling Components with the DevTools Profiler
* Virtualize Long Lists
* Avoid Reconciliation
* shouldComponentUpdate in Action
* The Power Of Not Mutating Data
* Using Immutable Data Structures 

## Reconciliation 

When a component's props or state change, React decides whether an actual DOM update is necessary by comparing the newly returned element with the previously rendered one. When they are not equal, React will update the DOM. This process is called Reconciliation. 

## The Diffing Algorithm

When diffing two trees, React first compares the two root elements. The behavior is different depending on the types of the root elements. 

React implements a heuristic O\(n\) algorithm based on two assumptions: 

* Two elements of different types will produce different trees
* The developer can hint at which child elements may be stable across different renders with a key prop.

## Shadow DOM

The Shadow DOM is a browser technology designed primarily for scoping variables and CSS in web components. 

## React Fiber

Fiber is new reconciliation engine in React 16. Its main goal is to enable incremental rendering of the virtual DOM.

## Framework vs Library

The key difference between a library and a framework is "Inversion of Control". When you call a method from a library, you are in control. However, with a framework, the control is inverted: the framework calls you. A library is just a collection of class definitions. 

## Steps for building React Project

* Break the UI into a Component Hierarchy
* Build a static version in React
* Identify the minimal \(but complete\) representation of UI state
* Identify where your state should live
* Add inverse Data Flow

[React Documentation](https://reactjs.org/docs/thinking-in-react.html)

## Compilers - Babel

A JavaScript compiler takes JavaScript code, transforms it and returns JavaScript code in a different format. The most common use case is to take ES6 syntax and transform it into syntax that older browsers are capable of interpreting.

## Bundlers - Webpack & Browserify

Bundlers take JavaScript and CSS code written as separate modules, and combine them together into a few files better optimized for the browsers. 

## Package Managers - NPM & Yarn

Package managers are tools that allow you to manager dependencies in your project. 

## Accessibility

* Semantic HTML
* Accessible Forms
* Focus Control
* Mouse and pointer events
* More Complex Widgets

## Strict Mode

StrictMode is a tool for highlighting potential problems in an application:

* Identifying components with unsafe lifecycles
* Warning about legacy string ref API usage
* Warning about deprecated findDOMNode usage
* Detecting unexpected side effects
* Detecting legacy context API 

## Test method

Jest and Enzyme



























 

























