# Performance Improvement

## Memoization

Use React.Memo:

export default React.memo\(\(props\) =&gt; { return \( {props.value}  
\) }\);



## useMemo

only {props.item} changes then someProp will recalculate.

function Component\(props\) { const someProp = useMemo\(\(\) =&gt; heavyCalculation\(props.item\), \[props.item\]\); return  }

## React.PureComponent , shouldComponentUpdate

PureComponent implemements shouldComponentUpdate\(\)  with a shallow prop and state comparison



const styles = { margin: 0 }; function Component\(props\) { const aProp = { someProp: 'someValue' } return   
}



## lazy loading

use suspense and lazy



## Use React Fragments

![](../.gitbook/assets/image%20%2888%29.png)



## Avoid Async in componentWillMount\(\) 



## constructor bind\(\)

this.functions\(\) = this.functions\(\).bind\(this\)

Bind the function in the constructor. Not in line binding.



## Avoid inline CSS

import CSS

## Use conditional rendering



Avoid output data/ setState in render\(\);



## Create ErrorBoundaries

import React from 'react';

export class ErrorBoundaries extends React.Component { constructor\(props\) { super\(props\); this.state = { hasErrors: false } }

```text
componentDidCatch(error, info) {
    console.dir("Component Did Catch Error");
}

static getDerivedStateFromError(error) {
    console.dir("Get Derived State From Error");
    return {
        hasErrors: true
    }
}

render() {

    if(this.state.hasErrors === true) {
        return <div>This is a Error</div>
    }

    return <div><ShowData name="Mayank" /></div>
}


export class ShowData extends React.Component {
    constructor() {    
        super();
        this.state = {
            name: "Mayank"
        }
    }
    
    changeData = () => {
       this.setState({
           name: "Anshul"
       })
    }
    render() {
    
        if(this.state.name === "Anshul") {
            throw new Error("Sample Error")
        }
    
        return (
            <div>
                <b>This is the Child Component {this.state.name}</b>
                <input type="button" onClick={this.changeData} value="Click To Throw Error" />
            </div>
        )
    }
}
```



Throttling and debouncing



CDN



CSS animation instead of javascript animation



use gzip compress



use web workers













