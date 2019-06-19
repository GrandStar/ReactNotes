# Redux

## Redux

Redux is an open-source JavaScript library for managing application state. The basic idea of redux is that the entire application state is kept in a single store. The store is simply a JavaScript object. The only way to change the state is by firing actions from your application and then writing reducers for these actions that modify the state. The entire state transition is kept inside reducers and should not have any side-effects. 

## How does Redux work

## Why use Redux

Application state management that is easy to reason about, maintain and manage in an asynchronous web application environment. 

## 3 fundamental principles

* Single source of truth - the state of your whole application is stored in an object tree within a single store.
* State is read-only - the only way to change the state is to emit an action, an object describing what happened.
* changes are made with pure functions - to specify how the state tree is transformed by actions, you write pure reducers. 

## Why Redux is immutable

State is read-only. The only way to change the state is to emit an action, an object describing what happened. Inside a Redux application there is one particular function that takes the previous state and the action being dispatched, and returns the next state of the whole application. Reducer is the function knowing how to return a new state based on the action it receives. 

## Why state is immutable in Redux

Redux's use of shallow equality checking requires immutability if any connected components are to be update correctly. Immutability can bring increased performance to your app, and leads to simpler programming and debugging, as data that never changes is easier to reason about than data that is free to be changed arbitrarily throughout your app. In particular, immutability in the context of a Web app enables sophisticated change detection techniques to be implemented simply and cheaply, ensuring the computationally expensive progress of updating the DOM occurs only when it absolutely has to. 

## Redux vs Context API

Context API is built into React and you therefore need no extra third-party dependencies. e.g. You don't need a package like redux-thunk to handle asynchronous actions. 

The Context API is not built for high-frequency updates. It's only recommend for low-frequency updates \(e.g. theme changes, user authentication\) but not use it for the general state management of your application. 

## Shallow Equality Check vs Deep Equality Check

Shallow equality checking \(or reference equality\) simply checks that two different variables reference the same object; in contrast, deep equality checking \(or value equality\) must check every value of two object's properties.  

A shallow equality check is therefore as simple and as fast as `a === b`, whereas a deep equality check involves a recursive traversal through the properties of two objects, comparing the value of each property at each step.

It's for this improvement in performance that Redux uses shallow equality checking. 

## Action

Actions are plain JavaScript objects. They must have a type indicating the type of action being performed. In essence, actions are payload of information that send data from your application to your store. 

## Reducer

A reducer is simply a pure function that takes the previous state and an action, and returns the next state. 

## Store

The store is a JavaScript object that holds application state. Along with this it also has the following responsibilities:

* Allows access to state via getState\(\)
* Allows state to be updated via dispatch\(action\)
* Registers listeners via subscribe\(listener\)
* Handles unregistering of listeners via the function returned by subscribe\(listener\)

The only way to change the state inside it is to dispatch an action on it. 

## Redux Thunk

Redux thunk is a middleware that allows you to write action creators that return a function instead of an action. The thunk can then be used to delay the dispatch of an action if a certain condition is met. This allows you to handle the asynchronous dispatching of actions. This also allows you to dispatch multiple actions. 

## createStore

Creates a Redux store that holds the complete state tree of your app. There should only be a single store in your app. 

* `reducer` - a reducing function that returns the next state tree, given the current state tree and an action to handle. 
* `[preloadedState]`- the initial state. 
* `[enhancer]`- the store enhancer. The only store enhancer that ships with Redux is `applyMiddleware()`

## combineReducers

The `combineReducers` helper function turns an object whose values are different reducing functions into a single reducing function you can pass to `createStore`.

## Middleware for handling asynchronous calls

Redux Thunk, Redux Promise, Redux Saga

## mapStateToProps vs mapDispatchToProps

Functions typically seen in Redux applications that provide functions to Redux on how to map state / dispatch function to a set of props. 

## Redux Saga vs Redux Thunk

Redux Thunk can never act in response to an action. Redux Saga, on the other hand, subscribes to the store and can trigger a saga to run or continue when a certain action is dispatched. 

## Component vs Container in React Redux

`Component` is part of the React API. A Component is a class or function that describes part of a React UI. 

`Container` is an informal term for a React component that is connected to a redux store. Containers receive Redux state updates and dispatch actions, and they usually don't render DOM elements, they delegate rendering to presentational child components. 

## React State vs Redux State

React state is stored locally within a component. When it needs to be shared with other components, it is passed down through props. 

When using Redux, state is stored globally in the Redux store. Any component that needs access to a value may subscribe to the store and gain access to that value. 





