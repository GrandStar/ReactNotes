---
description: >-
  REPL Node.js --Global Objects / util  - Global Objects / util----File System /
  HTTP-----express，mocha，npm
---

# NodeJS

## Node.JS

Node.JS is an open-source, cross-platform JavaScript runtime environment that executes JavaScript code server-side.

core is async I/O

Use async I/O not multi thread

like search:  db.query\('SELECT \* from some\_table', function\(res\) { res.output\(\); }\);

callback as second parameter. async -&gt; event loop, solve the block

everything is event loop

![](../.gitbook/assets/image%20%283%29.png)

Usage: node \[options\] \[ -e script \| script.js \] \[arguments\] 

e.g.: node debug script.js \[arguments\]

## REPL model

REPL stands for \(READ, EVAL, PRINT, LOOP\). NodeJS comes with bundled REPL environment. This allows for the easy creation of CLI \(Command Line Interface\) applications. 

```text
const repl = require('repl');
```

The `repl` module exports the [`repl.REPLServer`](https://nodejs.org/api/repl.html#repl_class_replserver) class. While running, instances of [`repl.REPLServer`](https://nodejs.org/api/repl.html#repl_class_replserver) will accept individual lines of user input, evaluate those according to a user-defined evaluation function, then output the result. 

* `.break` - When in the process of inputting a multi-line expression, entering the `.break` command \(or pressing the `<ctrl>-C` key combination\) will abort further input or processing of that expression.
* `.clear` - Resets the REPL `context` to an empty object and clears any multi-line expression currently being input.
* `.exit` - Close the I/O stream, causing the REPL to exit.
* `.help` - Show this list of special commands.
* `.save` - Save the current REPL session to a file: `> .save ./file/to/save.js`
* `.load` - Load a file into the current REPL session. `> .load ./file/to/load.js`
* `.editor` - Enter editor mode \(`<ctrl>-D` to finish, `<ctrl>-C` to cancel\).

## Express

Express.JS is a web application framework for Node.JS. It is designed for building web applications and APIs.

## NodeJS architecture 

Single Threaded Event Loop Model 

## How to do auth in NodeJS

Using Passport.js. Passport is authentication middleware for NodeJS. Passport can be easily dropped into any Express-based web applications. It's a comprehensive set of strategies supports authentication using a username and password, Facebook, Twitter. 

## The advantages of NodeJS server

* JavaScript as the programming language
* Asynchronous events
* Real-time web apps
* NPM package manager
* Data sharing
* Event driven architecture

## How to make HTTP request

* Default http, https module
* Request
* Axios
* SuperAgent
* Got

```text
http.get(options, (res) => {
  // Do stuff
}).on('socket', (socket) => {
  socket.emit('agentRemove');
});
```

## How does NodeJS handle child threads

NodeJS is a single thread process. It does not expose child threads and thread management methods to the developer. Technically, NodeJS does spawn child threads for certain tasks such as asynchronous I/O, but these run behind the scenes and do not execute any application JavaScript code, nor block the main event loop. If threading support is desired in a NodeJS application, there are tools available to enable it, such as the `ChildProcess` module. 

## How does NodeJS support multi-processor platforms

Since NodeJS is by default a single thread application, it will run on a single processor core and will not take full advantages of multiple core resources. However, NodeJS provides support for deployment on multiple-core systems, to take greater advantage of the hardware. The `Cluster` module is one of the core NodeJS modules and it allows running multiple NodeJS worker processes that will share the same port. 

## File System

To include the File System module, use the `require()` method.

* Read files - `fs.readFile()`
* Create files - `fs.appendFile(), fs.open(), fs.writeFile()`
* Update files - `fs.appendFile(), fs.writeFile()`
* Delete files - `fs.unlink()`
* Rename files - `fs.rename()`
* Upload files



## Util

The `util` module is primarily designed to support the needs of Node.js' own internal APIs. However, many of the utilities are useful for application and module developers as well. It can be accessed using:

```text
const util = require('util');
```

```text
const util = require('util');

async function fn() {
  return 'hello world';
}
const callbackFunction = util.callbackify(fn);

callbackFunction((err, ret) => {
  if (err) throw err;
  console.log(ret);
});
```

