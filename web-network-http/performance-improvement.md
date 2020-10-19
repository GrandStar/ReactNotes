---
description: 1. HTTP request   ...   2. JS loading(React)
---

# Performance Optimization

## 1 Use CDN. 

Like third party library, react, google earth. 

Async loading

## 2 Picture:

Use google WebP, SVG, or jpg/png. **Indexed Color. Direct Color. Bitmap**

####  HTTP2 next chapter

![](../.gitbook/assets/image%20%2898%29.png)

#### Use cache

#### IconFont

## 3. Compression

gzip: The gzip format is used in [HTTP compression](https://en.wikipedia.org/wiki/HTTP_compression), a technique used to speed up the sending of [HTML](https://en.wikipedia.org/wiki/HTML) and other content on the [World Wide Web](https://en.wikipedia.org/wiki/World_Wide_Web). It is one of the three standard formats for HTTP compression as specified in [RFC 2616](https://tools.ietf.org/html/rfc2616)

## 4: \(Loading\) Split Bundles

Use webpack **DllPlugin** to split big js file. [https://webpack.js.org/plugins/dll-plugin/](https://webpack.js.org/plugins/dll-plugin/)

Split third party dependencies and your code.

third party library: try to use CDN for not updated code.

Code: split by : first screen /  calls times / service and public module

## Asynchronous loading

First loading the core page.

## Preload

&lt;link rel="preload"&gt;  [https://developer.mozilla.org/en-US/docs/Web/HTML/Preloading\_content](https://developer.mozilla.org/en-US/docs/Web/HTML/Preloading_content)

The `preload` value of the [`<link>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/link) element's [`rel`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/link#attr-rel) attribute lets you declare fetch requests in the HTML's [`<head>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/head), specifying resources that your page will need very soon, which you want to start loading early in the page lifecycle, before browsers' main rendering machinery kicks in.



## Avoid inline CSS

import CSS

## React Memoization

Use React.Memo:

export default React.memo\(\(props\) =&gt; { return \( {props.value}  
\) }\);



## React useMemo

only {props.item} changes then someProp will recalculate.

function Component\(props\) { const someProp = useMemo\(\(\) =&gt; heavyCalculation\(props.item\), \[props.item\]\); return  }

## React.PureComponent , shouldComponentUpdate

PureComponent implemements shouldComponentUpdate\(\)  with a shallow prop and state comparison

const styles = { margin: 0 }; function Component\(props\) { const aProp = { someProp: 'someValue' } return   
}



## React lazy loading

use suspense and lazy



## Use React Fragments

![](../.gitbook/assets/image%20%2888%29.png)



## React Avoid Async in componentWillMount\(\) 



## React  constructor bind\(\)

this.functions\(\) = this.functions\(\).bind\(this\)

Bind the function in the constructor. Not in line binding.



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





CSS animation instead of javascript animation



use gzip compress



use web workers













