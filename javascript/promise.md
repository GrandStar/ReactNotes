# Promise

fullfill -&gt; resolve, reject, eventual value/value. reason.

![](../.gitbook/assets/image%20%2822%29.png)

* Promise represents the eventual completion of an async operation
* It must be in one of these states
  * pending
    * initial state, not fulfilled or rejected
  * fulfilled
    * meaning that the operation completed successfully
  * rejected
    * meaning that the operation failed
* It is guaranteed that a promise object will either succeed or fail
* promise.all 
  * returns a single promise that resolves when all of the promises in the argument have resolved or when the utterable argument contains no promises
* create Promise example

## Method:

[`Promise.all(iterable)`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/all)Wait for **all promises** to be resolved, or for any to be rejected. If the returned promise resolves, it is resolved with an aggregating array of the values from the resolved promises in the same order as defined in the iterable of multiple promises. 

[`Promise.race(iterable)`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise/race) ``Wait until **any o**f the promises is resolved or rejected. If the returned promise resolves, it is resolved with the value of the first promise in the iterable that resolved. If it rejects, it is rejected with the reason from the **first promise** that was rejected.

[`Promise.reject(reason)`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise/reject)

[`Promise.resolve(value)`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise/resolve)Returns a new `Promise` object that is resolved with the given value. 

```javascript
function asyncDoubble(n) {
    return new Promise((resolve, reject) => {
        if (typeof n === "number") {
            resolve(n * 2);
        } else {
            reject(new Error (n + "is not a number!"));
        }
    });
}
asyncDouble(3).then(
    data => console.log(data);
    error => console.log(error);
);
```



## Then\(\) method

```text
promise.then(onFulfilled, onRejected)
```

onFulfilled and  two function\(\)

onFulfilled\(a, \[\]\) : call after promise finished. the a is the return of promise 

onRejected\(a, \[\]\) : call after promise finished. the a is the reason of promise 

Then can be called multiply times: 

if resolve: onFulfilled call back one by one

if reject: onRejected call back one by one

## promise chain

```text
new Promise(function(resolve, reject) {

  setTimeout(() => resolve(1), 1000); // (*)

}).then(function(result) { // (**)

  alert(result); // 1
  return result * 2;

}).then(function(result) { // (***)

  alert(result); // 2
  return result * 2;

}).then(function(result) {

  alert(result); // 4
  return result * 2;

});
```

## Promise use observable module:

```text
class EventEmitter {
    constructor() {
        this.eventChannel = {};
    }
    on(event, callback) {
        this.eventChannel[event] ?
            this.eventChannel[event].push(callback) :
            this.eventChannel[event] = [callback]
    }
    emit(event, ...args) {
        this.eventChannel[event] && this.eventChannel[event].forEach(callback => callback(...args))
    }
    remove(event) {
        if (this.eventChannel[event]) {
            delete this.eventChannel[event]
        }
    }
    once(event, callback) {
        this.on(event, (...args) => {
            callback(...args);
            this.remove(event)
        })
    }
}
```

![](../.gitbook/assets/image%20%2880%29.png)



```javascript
class Observer {
    constructor() {
        this.observerList = [];
    }
    subscribe(observer) {
        this.observerList.push(observer)
    }
    notifyAll(value) {
        this.observerList.forEach(observe => observe(value))
    }
}


```

## Implement promise all, resolve, reject, race

```javascript
class Promise {
 state = 'pending'
  value = null
  reason = null

  onFulfilledCallback = []
  onRejectedCallback = []

  constructor(executor) {
    if (typeof executor !== 'function') {
      throw TypeError('executor is not a function!')
    }

    this.resolve = this.resolve.bind(this)
    this.reject = this.reject.bind(this)

    executor(this.resolve, this.reject)
  }

  
  finally(callback) {
    return this.then(
      () => Promise.resolve(callback()),
      () => Promise.reject(callback()),
    )
  }
 
}
```

### Promise all:

promises should be array of function

```javascript
static all(promises) {
    if (!promises || typeof promises[Symbol.iterator] !== 'function') {
      throw TypeError(
        `${typeof promises} is not iterable (cannot read property Symbol(Symbol.iterator))`,
      )
    }

    let index = 0
    const res = []

    return new Promise((resolve, reject) => {
      const n = promises.length
      if (!n) return []
      function processPromise(value, i) {
        res[i] = value
        if (++index === n) resolve(res)
      }

      for (let i = 0; i < n; i++) {
        Promise.resolve(promises[i]).then(
          (value) => {
            processPromise(value, i)
          },
          (reason) => {
            reject(reason)
          },
        )
      }
    })
  }
```

### Race

```javascript
class Promise {
  static race(promises) {
    if (!promises || typeof promises[Symbol.iterator] !== 'function') {
      throw TypeError(
        `${typeof promises} is not iterable (cannot read property Symbol(Symbol.iterator))`,
      )
    }

    if (!promises.length) {
      throw Error('Promise.race need length')
    }

    return new Promise((resolve, reject) => {
      for (const promise of promises) {
        Promise.resolve(promise).then(
          (value) => {
            resolve(value)
          },
          (reason) => {
            reject(reason)
          },
        )
      }
    })
  }
  
}


```

### Resolve

```javascript
resolve(value) {
    if (this.state === 'pending') {
      this.state = 'fulfilled'
      this.value = value

      this.onFulfilledCallback.forEach((fn) => {
        fn(this.value)
      })
    }
  }
```

### Reject

```javascript
reject(reason) {
    if (this.state === 'pending') {
      this.state = 'rejected'
      this.reason = reason

      this.onRejectedCallback.forEach((fn) => {
        fn(this.reason)
      })
    }
  }
```

### Then

```javascript
then(onFulfilled, onRejected) {
    if (typeof onFulfilled !== 'function') {
      onFulfilled = function (value) {
        return value
      }
    }
    if (typeof onRejected !== 'function') {
      onRejected = function (reason) {
        return reason
      }
    }

    const promise = new Promise((resolve, reject) => {
      if (this.state === 'fulfilled') {
        try {
          const result = onFulfilled(this.value)
          check(promise, result, resolve, reject)
        } catch (e) {
          reject(e)
        }
      }
      if (this.state === 'rejected') {
        try {
          const result = onRejected(this.reason)
          check(promise, result, resolve, reject)
        } catch (e) {
          reject(e)
        }
      }
      if (this.state === 'pending') {
        this.onFulfilledCallback.push((value) => {
          try {
            const result = onFulfilled(value)
            check(promise, result, resolve, reject)
          } catch (e) {
            reject(e)
          }
        })
        this.onRejectedCallback.push((reason) => {
          try {
            const result = onRejected(reason)
            check(promise, result, resolve, reject)
          } catch (e) {
            reject(e)
          }
        })
      }
    })
    return promise
  }
   function check(promise1, promise2, resolve, reject) {
    if (promise1 === promise2) {
      reject('Chaining cycle detected for Promise')
    } else {
      if (promise2 instanceof Promise) {
        promise2.then(resolve, reject)
      } else {
        resolve(promise2)
      }
    }
  }
}

```

