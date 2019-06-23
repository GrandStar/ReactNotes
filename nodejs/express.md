# express

## Basic 

const express = require\('express'\)

const app = express\(\)  
Add a new route method to handle requests for the path "/". The first argument specifies the path or URL, the next argument is the route handler. Inside the route handler, let's use the response object to send a status code 200 \(OK\) and text to the client

app.get\('/', \(request, response, nextHandler\) =&gt; {

response.status\(200\).send\('Hello from ExpressJS'\)

}\)

Finally, use the listen method to accept new connections on port 1337:

app.listen\(1337, \(\) =&gt; console.log\('Web Server running on port 1337'\),\)



## Express

create new 

```text
var express = require('express');
var app = express();

app.get('/', function(req, res){
  res.send('hello world');
});

app.listen(3000);
```



## Router :

Routing refers to determining how an application responds to a client request to a particular endpoint, which is a URI \(or path\) and a specific HTTP request method \(GET, POST, and so on\).

```text
app.METHOD(PATH, HANDLER);
```

A `router` object is an isolated instance of middleware and routes. You can think of it as a “mini-application,” capable only of performing middleware and routing functions. Every Express application has a built-in app router

CRUD

```text
// GET method route
app.get('/', function (req, res) {
  res.send('GET request to the homepage');
});

// POST method route
app.post('/', function (req, res) {
  res.send('POST request to the homepage');
});
```

```text
app.put('/user', function(req, res) {
  res.send('Got a PUT request at /user');
});
```

```text
app.delete('/user', function(req, res) {
  res.send('Got a DELETE request at /user');
});
```

![](../.gitbook/assets/image%20%289%29.png)

![](../.gitbook/assets/image%20%2837%29.png)

![](../.gitbook/assets/image%20%283%29.png)

![](../.gitbook/assets/image%20%2836%29.png)

Respond to all METHOD to the /user route:

```text
app.all('/user', function(req, res) {
  res.send('Got a request at /user');
});
```



```text
const express = require('express');
const router = express.Router();

// middleware that is specific to this router
router.use(function timeLog(req, res, next) {
  console.log('request for books - Time: ', Date.now());
  next();
});
// define the home page route
router.get('/', function(req, res) {
  res.send('Books home page');
});
// define the about route
router.get('/about', function(req, res) {
  res.send('About books');
});

module.exports = router;
```



## app.use\(\[path\], function\)\]

```text
var express = require('express');
var app = express();

// 一个简单的 logger
app.use(function(req, res, next){
  console.log('%s %s', req.method, req.url);
  next();
});

// 响应
app.use(function(req, res, next){
  res.send('Hello World');
});

app.listen(3000);
```

static:, ./public static service

```text
app.use(express.static(__dirname + '/public'));
```

## app.all\(path, \[callback...\], callback\)

match all HTTP active

## Handling error

In Express, 404 responses are not the result of an error, so the error-handler middleware will not capture them. This behavior is because a 404 response simply indicates the absence of additional work to do; in other words, Express has executed all middleware functions and routes, and found that none of them responded. All you need to do is add a middleware function at the very bottom of the stack \(below all other functions\) to handle a 404 response:

```text
app.use(function(req, res, next) {
  res.status(404).send("Sorry can't find that!");
});

app.use(function(err, req, res, next) {
  console.error(err.stack);
  res.status(500).send('Something broke!');
});
```



## Express Middleware

Middleware functions are functions that have access to the request object \(req\), the response object \(res\), and the next middleware function in the application’s request-response cycle. The next middleware function is commonly denoted by a variable named next.

Middleware functions can perform the following tasks:

* Execute any code.
* Make changes to the request and the response objects.
* End the request-response cycle.
* Call the next middleware function in the stack.

middleware e.g.

function: redirect\('/login'\);

```text
app.use(function(req, res, next) {
  if (req.isAuthenticated) {
    next();
  } else {
    res.redirect('/login');
  }
});
```

```text
// define the home page route
router.get('/', function(req, res) {
  res.send('Books home page');
});
```

**Example - Error Handling**

You define error-handling middleware in the same way as other middleware, except with four arguments instead of three; specifically with the signature \(err, req, res, next\):

```text
app.use(function(err, req, res, next) {
  console.error(err.stack);
  res.status(500).send('Something broke!');
});
```

