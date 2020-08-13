# Lifting functions/ state up

One very important descision every react developer has to make is how to structure the app and which component will be responsible for holding the data.

Because data can cause elements to re-render we should keep data as low down in the tree of elements as possible. This keeps each piece as separate and modular as possible.

There will be many cases in which the data that you use in one component in the tree is needed in a _sibling_ component.

![](../.gitbook/assets/image%20%2869%29.png)

For this example let's take the `Line` component.

There could be many features that are implemented in this component:

* conditional rendering of the drop down options
* rendering the drop down options from an ajax call to get train line conditions
* etc., etc.

However, from the wireframe it's most likely that the drop down affects the main `Predictions` component.

In this case, where the selected line affects another sibling component, where do you store that state?

The lowest place in the element tree with these two components in common is actually still at the top level of this page. \(Which is fine, and mostly unavoidable\)

In this case we have to store the actual state in the top level.

The technique for doing this is called "lifted" functions.

**Lifted Functions**

If we want state to be available for 2 sibling components, we have to store it in the closest parent.

In order to set state on a parent component we _must_ call a method on the parent component.

When the state is set on the parent, it will pass back down the data set in the method.  


```text
class App extends React.Component{

    constructor(){
        super();
        this.state = {
            station : "banana"
        };

    }

  setCurrentStation(station){
    this.setState({station})
  }

  render(){
    return (
      <div>
        <Line setCurrentStation={(s)=>{this.setCurrentStation(s)}} station={this.state.station}/>
        <Trains station={this.state.station}/>
      </div>
    );
  }
}

class Line extends React.Component{

  render(){
    return (
      <div>
        <h1>{this.props.station}</h1>
        <button onClick={this.props.setCurrentStation}/>
      </div>
    );
  }
}

class Trains extends React.Component{

  render(){
    return (
      <div>
        <h1>{this.props.station}</h1>
      </div>
    );
  }
}
```

