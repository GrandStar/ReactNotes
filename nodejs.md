# NodeJS

## Node.JS

Node.JS is an open-source, cross-platform JavaScript runtime environment that executes JavaScript code server-side.

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

## REPL

REPL stands for \(READ, EVAL, PRINT, LOOP\). NodeJS comes with bundled REPL environment. This allows for the easy creation of CLI \(Command Line Interface\) applications. 

