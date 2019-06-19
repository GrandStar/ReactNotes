# Restful API

## Map CRUD to HTTP methods on a RESTful API

* Create - Post
* Read - Get
* Update - Put
* Delete - Delete

## The difference between PUT, POST and PATCH method

## HTTP Status Code

* 1xx: Informational
* 2xx: Success
* 3xx: Redirection
* 4xx: Client Error
* 5xx: Server Error

## MVC vs Flux

MVC works both in server and client side development. MVC architecture: the user updates the controller, the controller manipulates the model, the model updates the view, and finally the user can see the view.

Flux is used for building client-side web applications. It implements React's com-posable view components by utilizing a unidirectional data flow. 

## Throw vs Reject

Any time you are inside a promise callback, you can use `throw`. However, if you are in any other asynchronous callback, you must use `reject`. Moreover, `reject` does not terminate control flow like a `return` statement does. In contrast `throw` does terminate control flow.

## AJAX

AJAX \(Asynchronous JavaScript and XML\) is to create asynchronous web applications. With AJAX, web applications can send data and retrieve from a server asynchronously in the background without the need to reload the entire page. 

The `XMLHttpReques`t API is frequently used for the asynchronous communication or these days, the `fetch` API. 

## AJAX - pros & cons

Advantages:

* Better interactivity. New content from the server can be changed dynamically without the need to reload the entire page. 
* Reduce connections to the server since scripts and stylesheets only have to be requested once. 
* State can be maintained on a page. JavaScript variables and DOM state will persist because the main container page was not reloaded.
* Basically most of the advantages of an SPA.

Disadvantages:

* Dynamic webpages are harder to bookmark.
* Does not work if JavaScript has been disabled in the browser.
* Some web-crawlers do not execute JavaScript and would not see content that has been loaded by JavaScript. 
* Basically most of the disadvantages of an SPA. 

## Cross Browser Compatibility Issues

Since difference browser may require different API for the same functionality, you can easily use if - else statement to define which API should be used in which environment. If the API is not working with that browser, it will return undefined. 

## Continuous Integration \(CI\)

Continuous Integration is a development practice that requires developers to integrate code into a shared repository several times a day. Each check-in is then verified by an automated build, allowing teams to detect problems early. 

## Cross-Domain Solution \(CDS\)

A cross-domain solution is a means of information assurance that provides the ability to manually or automatically access or transfer information between two or more differing security domains. 

## Cross-Origin Resource Sharing \(CORS\)

Cross-Origin Resource Sharing \(CORS\) is a mechanism that uses additional HTTP headers to tell a browser to let a web application running at one origin \(domain\) have permission to access selected resources from a server at a different origin. A web application executes a cross-origin HTTP request when it requests a resource that has a different origin \(domain, protocol, and port\) than its own origin. 

## 5 ways to reduce the page loading speed

* Optimize Images
* Browser Caching 
* Compression
* Optimize Your CSS
* Keep the Scripts below the fold

## The workflow for JSON web token

![](.gitbook/assets/image%20%281%29.png)

## How do you parse JSON in backend

use body-parser module

## Microservices 

Microservices - also known as microservice architecture - is an architectural style that structures an application as a collection of services that are 

* Highly maintainable and testable 
* Loosely coupled
* Independently deployable
* Organized around business capabilities

The microservice architecture enables the continuous delivery/deployment of large, complex applications. It also enables an organization to evolve its technology stack. 



