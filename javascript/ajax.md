---
description: >-
  AJAXRead data from a web server - after the page has loadedUpdate a web page
  without reloading the pageSend data to a web server - in the background
---

# AJAX

### XMLHttpRequest Object

All modern browsers \(Chrome, Firefox, IE7+, Edge, Safari, Opera\) have a built-in `XMLHttpRequest` object.

Syntax for creating an `XMLHttpRequest` 

var xhttp = new XMLHttpRequest\(\);

request

```text
$.ajax({
  url: "http://localhost:8080/login",
  type: 'GET',
  // Fetch the stored token from localStorage and set in the header
  headers: {"Authorization": localStorage.getItem('token')}
});

$.ajax({
  url: "http://localhost:8080/login",
  type: "POST",
  headers: { Authorization: $`Bearer ${localStorage.getItem("token")}` },
  data: formData,
  error: function(err) {
    switch (err.status) {
      case "400":
        // bad request
        break;
      case "401":
        // unauthorized
        break;
      case "403":
        // forbidden
        break;
      default:
        //Something bad happened
        break;
    }
  },
  success: function(data) {
    console.log("Success!");
  }
});
```



### XMLHttpRequest Object Methods

| Method | Description |
| :--- | :--- |
| new XMLHttpRequest\(\) | Creates a new XMLHttpRequest object |
| abort\(\) | Cancels the current request |
| getAllResponseHeaders\(\) | Returns header information |
| getResponseHeader\(\) | Returns specific header information |
| open\(_method, url, async, user, psw_\) | Specifies the request  _method_: the request type GET or POST _url_: the file location _async_: true \(asynchronous\) or false \(synchronous\) _user_: optional user name _psw_: optional password |
| send\(\) | Sends the request to the server Used for GET requests |
| send\(_string_\) | Sends the request to the server. Used for POST requests |
| setRequestHeader\(\) | Adds a label/value pair to the header to be sent |

### XMLHttpRequest Object Properties

| Property | Description |
| :--- | :--- |
| onreadystatechange | Defines a function to be called when the readyState property changes |
| readyState | Holds the status of the XMLHttpRequest. 0: request not initialized 1: server connection established 2: request received 3: processing request 4: request finished and response is ready |
| responseText | Returns the response data as a string |
| responseXML | Returns the response data as XML data |
| status | Returns the status-number of a request 200: "OK" 403: "Forbidden" 404: "Not Found" For a complete list go to the [Http Messages Reference](https://www.w3schools.com/tags/ref_httpmessages.asp) |
| statusText | Returns the status-text \(e.g. "OK" or "Not Found"\) |



## Send a Request To a Server

To send a request to a server, we use the open\(\) and send\(\) methods of the `XMLHttpRequest` object:xhttp.open\("GET", "ajax\_info.txt", true\);  
xhttp.send\(\);

| Method | Description |
| :--- | :--- |
| open\(method, url, async\) | Specifies the type of request  method: the type of request: GET or POST url: the server \(file\) location async: true \(asynchronous\) or false \(synchronous\) |
| send\(\) | Sends the request to the server \(used for GET\) |
| send\(string\) | Sends the request to the server \(used for POST\) |

A simple `GET` request:

xhttp.open\("GET", "demo\_get.asp", true\);  
xhttp.send\(\);

xhttp.open\("GET", "demo\_get2.asp?fname=Henry&lname=Ford", true\); xhttp.send\(\);





```text
fetch('http://example.com/movies.json')
  .then(function(response) {
    return response.json();
  })
  .then(function(myJson) {
    console.log(myJson);
  });
```

