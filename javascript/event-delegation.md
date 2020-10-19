---
description: 'https://www.cnblogs.com/bfgis/p/5460191.html'
---

# Event DOM and delegation

## 3 type of event model: 

dom0 model, dom2 model, IE event model

## dom 0 event model:

 1. bind use element property:

```text
<button onclick="click()">click</button>
```

2. get the element, then bind it using adding values.

```text
const btn = document.getElementById('btn')
btn.onclick = function(){// do }
btn.onclick = null 
```

this will not spread, only bind 1 event

## Dom2 event model:

### 3 process in each event: capture, process, bubbling

use addEventListener\(\) to add event listener

![](../.gitbook/assets/image%20%2896%29.png)

## IE event model

### 2 process, no capture, process and bubbling

use attachEvent\(\) to add event listener

## capturing

[Here’s an example.](https://codepen.io/cferdinandi/pen/pqJZdK)

```text
document.addEventListener('focus', function (event) {
	console.log(event.target);
}, false);
```

You can focus on things over and over again, but the event callback will never run.

There’s a trick you can use to _capture_ the event, though. The last argument in `addEventListener()` is called `useCapture`. We almost always set it to false.

For events that don’t bubble, set it to `true` to capture the event anyways.

## Bubbling

When an event triggers on a DOM element, it will attempt to handle the vent if there is a listener attached, then the event is bubbled up to its parent and the same thing happens. The bubbling occurs up the element's ancestors all the way to the document. Event bubbling is the mechanism behind event delegation. 

```text
var logEvent = function(event) {
    console.log(event.target);
};
document.querySelector('main').addEventListener('input', logEvent, false);
document.querySelector('div').addEventListener('input', logEvent, false);
document.querySelector('input').addEventListener('input', logEvent, false);
```

## How to stop Event bubbling and capturing during Event delegation

e.stopPropagation\(\)

## Event Delegation vs Event Bubbling

Event delegation is a technique for listening to events where you delegate a parent element as the listener for all of the events that happen inside it.

Event bubbling is what the event itself does.

## delegation 委托

delegation element events to other elements using bubbling. 

you select any one of a large number of child elements, you can set the event listener on their parent and have events that happen on them bubble up to their parent rather than having to set the event listener on every child individually.

Remember, bubbling involves checking the element the event is fired on for an event handler first, then moving up to the element's parent, etc.

　　_**addEventListener\(event, listener, useCapture\)**_　　

useCapture : true: capturing,      useCapture = false : bubbling

Event delegation is a technique for listening to events where you _delegate_ a parent element as the listener for all of the events that happen inside it.

Event delegation is a technique involving adding event listeners to a parent element instead of adding them to the descendant elements. The listener will fire whenever the event is triggered on the descendant elements due to event bubbling up the DOM. 

The benefits of this technique are:

* **Memory** footprint goes down \(because only one single handler is needed on the parent element, rather than having to attach event handlers on each descendant\)
* **dynamics binding** There is no need to unbind the handler from elements that are removed and to bind the event for new elements. 

For example, if you wanted to detect any time any field changed in value inside a specific form, you could do this:

```text
var form = document.querySelector('#hogwarts-application');

// Listen for changes to fields inside the form
form.addEventListener('input', function (event) {

	// Log the field that was changed
	console.log(event.target);

}, false);
```

[https://learn.jquery.com/events/event-delegation/](https://learn.jquery.com/events/event-delegation/)

## 

