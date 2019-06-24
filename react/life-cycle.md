# Life Cycle

## React Lifecycle Methods 

Lifecycle methods are various methods which are invoked at different phases of the lifecycle of a component.



Mounting 

* constructor\(\)
* static getDerivedStateFromProps\(\)
* render\(\)
* componentDidMount\(\) - runs after the component output has been rendered to the DOM. 

Updating

* static getDerivedStateFromProps\(\)
* shouldComponentUpdate\(\)
* render\(\)
* getSnapshotBeforeUpdate\(\)
* componentDidUpdate\(\)

Unmounting

* componentWillUnmount\(\)

Error Handling

* static getDerivedStateFromError\(\)
* componentDidCatch\(\)
* * **render** This is the required method in a React component, as this method prepares the element that gets mounted on to the browser DOM. This method is pure, which means it gives the same output every time the same input is provided. This method should not result in any side effect like changing state.
* **componentDidMount** This is the hook method which is invoked immediately after the component **did** mount on the browser DOM.  **Usage:** All the interaction directly with the browser DOM and integrate with third-party libraries like Highcharts or D3 should be done here. E.g This method is best to draw sound wave graphs of songs.
* _The API calls should be made in componentDidMount method always._

![](../.gitbook/assets/image%20%2834%29.png)

**Mounting**

In React realm mounting refers to the loading of components on the DOM. This phase contains a set of methods which get invoked when the component is getting initialized, and loaded on to the DOM.

* **constructor** This is the first method that gets called whenever a component is created. The constructor is called only once in the whole lifecycle of a component. It’s used to set up the initial values of variables and component state.  **Usage**_**:**_ ****Setup the initial state of the component.

**static getDerivedStateFromProps**  
As the name suggests **get**ting the **derived** **state from props** is used when the state is dependent on props, hence whenever the props are changed the state has to be kept in sync.  
This method is invoked after the constructor and is expected to return an object to update the state of the component. If null is returned then, nothing is changed in the state.

The method `getDerivedStateFromProps` is static, hence it has no access to `this`

**Updating**

This phase starts when the react component has taken birth on the browser and grows by receiving new updates. The component can be updated in two ways, sending new props from parents or updating the current state.

The list of methods that will get called in sequence when the update happens in either way:

* **static getDerivedStateFromProps** This method behaves exactly as defined above in mounting phase.
* **shouldComponentUpdate** This method tells React that when the component is being updated, it should re-render or skip rendering altogether. This method is a question, **should** the **Component** be **Updated**?  Hence this **method should return true or false,** and accordingly, the component would be re-rendered or skipped.  By default, this method returns **true.** _**Usage:**_ The example is one of the cases where the render is quite costly and we would like to re-render the component only when the props status changes.
* **render** And then the component gets rendered \(details in mounting phase\).
* **getSnapshotBeforeUpdate**

![](../.gitbook/assets/image%20%2814%29.png)

  
****This method gets called after the render created the React element and before it is actually updated from virtual DOM to actual DOM. This phase is known as `pre-commit` phase.

* This method has access to both previous and current props and state. If the method `getSnapshotBeforeUpdate` returns a value, the same is available in `componentDidUpdate` as the third parameter, where the UI can be updated to make is synced before and after render.  **Usage:** This method is useful if you want to keep sync in-between state of current DOM with the updated DOM. E.g. scroll position, audio/video, text-selection, cursor position, tool-tip position, etc.
* **componentDidUpdate** is executed when the newly updated component has been updated in the DOM. This method is used to re-trigger the third party libraries used, and to make sure these libraries also update and reload themselves.
*   **3\) Unmounting**

  In this phase, the component is not needed and the component will get unmounted from the DOM.  
  Below is the method called in this phase:

  * **componentWillUnmount** This method is the last method in the lifecycle. This is executed just before the component gets removed from the DOM. ****_**Usage:**_ In this method, we do all the cleanups related to the component.  For example, on log out, the user details and all the auth tokens can be cleared before unmounting the main component.

## Old Life Cycle

![](../.gitbook/assets/image%20%2827%29.png)

