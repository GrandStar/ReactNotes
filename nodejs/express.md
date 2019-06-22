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

