---
description: 'https://developer.mozilla.org/en-US/docs/Web'
---

# WEB Network HTTP etc

## What's happened when you input URL in browser

[https://github.com/i-want-offer/FE-Essay/blob/master/%E6%B5%8F%E8%A7%88%E5%99%A8%E6%B8%B2%E6%9F%93/%E6%B5%8F%E8%A7%88%E5%99%A8%E8%BE%93%E5%85%A5URL%E7%9A%84%E5%85%A8%E8%BF%87%E7%A8%8B.md](https://github.com/i-want-offer/FE-Essay/blob/master/%E6%B5%8F%E8%A7%88%E5%99%A8%E6%B8%B2%E6%9F%93/%E6%B5%8F%E8%A7%88%E5%99%A8%E8%BE%93%E5%85%A5URL%E7%9A%84%E5%85%A8%E8%BF%87%E7%A8%8B.md)

## OAuth, OpenID Connect, and SAML

**OAuth** 

an application can take actions or access resources from a server on behalf of the user, without them having to share their credentials. It does this by allowing the [identity provider \(IdP\)](https://www.okta.com/identity-101/why-your-company-needs-an-identity-provider/) to issue tokens to third-party applications with the user’s approval.

op**enid**

OpenID Connect 1.0 is a simple identity layer on top of the OAuth 2.0 protocol. It allows Clients to verify the identity of the End-User based on the authentication performed by an Authorization Server, as well as to obtain basic profile information about the End-User in an interoperable and REST-like manner.

**saml**

enables you to log into your corporate intranet or IdP and then access numerous additional services, such as Salesforce, Box, or Workday, without having to re-enter your credentials. SAML is an XML-based standard for exchanging authentication and authorization data between IdPs and service providers to verify the user’s identity and permissions, then grant or deny their access to services.

## CSRF Protection

[cross-site request forgery](https://en.wikipedia.org/wiki/Cross-site_request_forgery) \(CSRF\) attacks. Cross-site request forgeries are a type of malicious exploit whereby unauthorized commands are performed on behalf of an authenticated user.

To [prevent CSRF](https://www.owasp.org/index.php/Cross-Site_Request_Forgery_%28CSRF%29_Prevention_Cheat_Sheet) you need a value that is submitted with the request that cannot be sent by a malicious site. Authentication cookies are not suitable because if an attacker can make the browser send a request to the victim site, the cookies will automatically be submitted.

For example, by submitting a form via JavaScript contained on `www.evil.com` to attack the user's session on `www.example.com`:

```text
<form method="post" action="https://www.example.com/executeAction">
    <input type="hidden" name="action" value="deleteAllUsers">
</form>

<script>document.forms[0].submit()</script>
```

CSRF tokens normally go in a form as hidden form fields. Putting them in a meta tag only makes sense if you are using JavaScript. JavaScript could read the tokens from the meta tag and post them to an action.

You wouldn't want to put a CSRF token in a cookie because the cookie will be sent for every request to the specific website from the web browser regardless of its origin. The only exception would be _secure cookies_, which are supposed to follow the same-origin policy.

## [Logging vs Tracing vs Monitoring ](https://winderresearch.com/logging-vs-tracing-vs-monitoring/)

### Logging <a id="logging"></a>

We use logging to represent state transformations within an application. When things go wrong, we need logs to establish what change in state caused the error.

But the problem is that obtaining, transferring, storing and parsing logs is expensive. Because of this it is crucial to only log what is necessary; only logs that can be acted upon should be stored. Log only actionable information.

This usually results in two types of data; panic-level information for humans and structured data for machines. I would also question whether you really need the structured data. But there are use cases, e.g. security.

### Tracing <a id="tracing"></a>

A trace represents a single user’s journey through an entire stack of an application. It is often used for optimisation purposes. For example you would use it to establish little used part of a stack or bottlenecks within specific parts of the stack.

But it adds significant complexity. There are often significant amounts of implementation code and is often designed as a push model, which means that applications could be affected by loading in the monitoring system.

The libraries intended to simplify tracing are often more complicated than the code they are serving.

Therefore tracing tends to be quite expensive. Think long and hard whether the added complexity is warranted. Are you falling into the trap of premature optimisation? Is optimisation that important when you could just scale horizontally?

### Instrumentation and Monitoring <a id="instrumentation-and-monitoring"></a>

**Monitor all the things!**

Instrumenting an application and monitoring the results represents the use of a system. It is most often used for diagnostic purposes. For example we would use monitoring systems to alert developers when the system is not operating “normally”.

Instrumentation tends to be very cheap to compute. Metrics take nanoseconds to update and some monitoring systems operate on a “pull” model, which means that the service is not affected by monitoring load.

Generally the more data you have, the more useful monitoring becomes.

So typically you would want to instrument all of your services. But make sure you pick a simple, scalable monitoring system like Prometheus!

In short, Monitoring != Logging != Tracing.

## WebAssembly

WebAssembly is a new type of code that can be run in modern web browsers — it is a low-level assembly-like language with a compact binary format that runs with near-native performance and provides languages such as C/C++ and Rust with a compilation target so that they can run on the web. It is also designed to run alongside JavaScript, allowing both to work together.

it provides a way to run code written in multiple languages on the web at near native speed, with client apps running on the web that previously couldn’t have done so.

[Compiling a New C/C++ Module to WebAssembly](https://developer.mozilla.org/en-US/docs/WebAssembly/C_to_wasm)

The web platform can be thought of as having two parts:

* A virtual machine \(VM\) that runs the Web app’s code, e.g. the JavaScript code that powers your apps.
* A set of [Web APIs](https://developer.mozilla.org/en-US/docs/Web/API) that the Web app can call to control web browser/device functionality and make things happen \([DOM](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model), [CSSOM](https://developer.mozilla.org/en-US/docs/Web/API/CSS_Object_Model), [WebGL](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API), [IndexedDB](https://developer.mozilla.org/en-US/docs/Web/API/IndexedDB_API), [Web Audio API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Audio_API), etc.\).

Historically, the VM has been able to load only JavaScript.

WebAssembly is a different language from JavaScript, but it is not intended as a replacement. Instead, it is designed to complement and work alongside JavaScript, allowing web developers to take advantage of both languages' strong points

#### WebAssembly key concepts

There are several key concepts needed to understand how WebAssembly runs in the browser. All of these concepts are reflected 1:1 in the [WebAssembly JavaScript API](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/WebAssembly).

* **Module**: Represents a WebAssembly binary that has been compiled by the browser into executable machine code. A Module is stateless and thus, like a [Blob](https://developer.mozilla.org/en-US/docs/Web/API/Blob), can be explicitly shared between windows and workers \(via [`postMessage()`](https://developer.mozilla.org/en-US/docs/Web/API/MessagePort/postMessage)\). A Module declares imports and exports just like an ES2015module.
* **Memory**: A resizable ArrayBuffer that contains the linear array of bytes read and written by WebAssembly’s low-level memory access instructions.
* **Table**: A resizable typed array of references \(e.g. to functions\) that could not otherwise be stored as raw bytes in Memory \(for safety and portability reasons\).
* **Instance**: A Module paired with all the state it uses at runtime including a Memory, Table, and set of imported values. An Instance is like an ES2015 module that has been loaded into a particular global with a particular set of imports.







## Cross-Origin Resource Sharing \([CORS](https://developer.mozilla.org/en-US/docs/Glossary/CORS)\) 

Cross-Origin Resource Sharing \([CORS](https://developer.mozilla.org/en-US/docs/Glossary/CORS)\) is a mechanism that uses additional [HTTP](https://developer.mozilla.org/en-US/docs/Glossary/HTTP) headers to tell a browser to let a web application running at one origin \(domain\) have permission to access selected resources from a server at a different origin. A web application executes a **cross-origin HTTP request** when it requests a resource that has a different origin \(domain, protocol, and port\) than its own origin.

 **HTTP head**

**Access-Control-Allow-Origin**

```text
Access-Control-Allow-Origin: <origin> | *


Access-Control-Allow-Origin: *
Access-Control-Allow-Origin: http://foo.example


app.all('/demo-normal', function(req, res) {
  res.header('Access-Control-Allow-Origin', '*');
  res.send('Hello World!');
});

app.all('/demo-credentials-can-work', function(req, res) {
  res.header('Access-Control-Allow-Origin', req.headers.origin);
  res.header('Access-Control-Allow-Credentials', 'true');
  res.send('Hello World!');
});
```

Access-Control-Allow-Credentials Access-Control-Allow-Methods

![](../.gitbook/assets/image%20%2828%29.png)

An example of a cross-origin request: The frontend JavaScript code for a web application served from `http://domain-a.com` uses [`XMLHttpRequest`](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest) to make a request for `http://api.domain-b.com/data.json`.

![](../.gitbook/assets/image%20%2832%29.png)

{% embed url="http://www.example.com:80/path/to/myfile.html?key1=value1&key2=value2\#SomewhereInTheDocument" %}

`http` is the protocol.

`www.example.com` is the domain name. 

`:80` is the port. 

`/path/to/myfile.html` is the path to the resource on the Web server.

`?key1=value1&key2=value2` are extra parameters provided to the Web server. 

`#SomewhereInTheDocument` is an anchor to another part of the resource itself. 

| **Scheme:** | **//** | **Login:password@** | **Address** | **:port** | **/path/to/resource** | **?query\_string** | **\#fragment** |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |






## **Internet Protocol version 6** \(**IPv6**\) 

![](../.gitbook/assets/image%20%2884%29.png)

Pv6 uses a 128-bit address, theoretically allowing 2^128 addresses.

The two protocols are not designed to be [interoperable](https://en.wikipedia.org/wiki/Interoperable)

![Glossary of terms used for IPv6 addresses.](../.gitbook/assets/image%20%2879%29.png)

![](../.gitbook/assets/image%20%2872%29.png)

### Comparison with IPv4:

#### Larger address space

#### Multicasting

![](../.gitbook/assets/image%20%2864%29.png)

[Multicasting](https://en.wikipedia.org/wiki/Multicast), the transmission of a packet to multiple destinations in a single send operation, is part of the base specification in IPv6.

#### Stateless address autoconfiguration \(SLAAC\) SLAAC

IPv6 hosts configure themselves automatically. Every interface has a self-generated link-local address and, when connected to a network, conflict resolution is performed and routers provide network prefixes via router advertisements.

#### IPsec

The IPsec Authentication Header \(AH\) and the Encapsulating Security Payload header \(ESP\) are implemented as IPv6 extension headers





## Validating a REST API

#### Validating HTTP Response Codes

* **200 OK:** no additional information is provided
* **201 Created:** a new data item was created on the server
* **202 Accepted:** the server has received the request, but hasn’t finished processing it
* **203 Non-Authorative Information:** a proxy server sent the response based on a response from the endpoint server, but the response isn’t identical to the response the proxy received
* **204 No Content:** the server processed the request and returned no content
* **205 Reset Content:** like 204, but the requester should reset its data view
* **206 Partial Content:** the content is a subset of the entire data set because the request asked for this
* **207 Multi-Status:** the response body is an XML document containing additional status information
* **208 Already Reported:** a follow-on related to 207
* **226 IM Used:** the response is a representation of one or more instance manipulations \(IMs\) applied to the current instance

**Validating HTTP Headers**

![](../.gitbook/assets/image%20%2857%29.png)

The `Content-Type` header illustrates the value of applying JavaScript to validate headers. If your application expects to receive a [JSON](http://www.json.org/) \(JavaScript Object Notation\) response body, then from the point of view of your application, this API is down if the response’s `Content-Type` header doesn’t include `application/json`.

#### Timing-Out Slow-Performing API Requests

#### Time-outs with Respect to Data Size

#### Using JavaScript to Validate API Response Bodies

#### Using Regular Expressions and JavaScript to Validate API Responses



[query-auth](https://github.com/jeremykendall/query-auth)

Websocket

![](../.gitbook/assets/image%20%2856%29.png)

## TCP 3-Way Handshake Process

![](../.gitbook/assets/image%20%2889%29.png)

* **Step 1 \(SYN\) :** In the first step, client wants to establish a connection with server, so it sends a segment with SYN\(Synchronize Sequence Number\) which informs server that client is likely to start communication and with what sequence number it starts segments with
* **Step 2 \(SYN + ACK\):** Server responds to the client request with SYN-ACK signal bits set. Acknowledgement\(ACK\) signifies the response of segment it received and SYN signifies with what sequence number it is likely to start the segments with
* **Step 3 \(ACK\) :** In the final part client acknowledges the response of server and they both establish a reliable connection with which they will start the actual data transfer

The steps 1, 2 establish the connection parameter \(sequence number\) for one direction and it is acknowledged. The steps 2, 3 establish the connection parameter \(sequence number\) for the other direction and it is acknowledged. With these, a full-duplex communication is established.

![](../.gitbook/assets/image%20%2890%29.png)

why 4 way to disconnect?

Cause client need verify server is ending data transfer.

![](../.gitbook/assets/image%20%2858%29.png)





{% embed url="https://www.ruanyifeng.com/blog/2017/05/websocket.html" %}

##  microservice

A microservice architecture involves many services that are each responsible for a small amount of functionality.

These services must communicate with each other over a network; since such communication would not be necessary in other architectures \(e.g. monolithic\), lower network latency is **not** a claimed benefit of microservice architecture.

Since the services are mostly self-contained, there’s less coupling and improved modularity between the various services.

By distributing functionality among multiple services, failure in part of the system does not necessarily result in failure of the entire system; this graceful degradation can lead to improved resiliency against failures. Furthermore, a microservice architecture makes it easier to introduce redundancy for critical components.

Finally, since it’s easier for developers to work on a particular service without affecting the rest of the system, it’s also easier to achieve continuous delivery.



## UTF 8

It was designed for [backward compatibility](https://en.wikipedia.org/wiki/Backward_compatibility) with [ASCII](https://en.wikipedia.org/wiki/ASCII). Code points with lower numerical values, which tend to occur more frequently, are encoded using fewer bytes. The first 128 characters of Unicode, which correspond one-to-one with ASCII, are encoded using a single byte with the same binary value as ASCII, so that valid ASCII text is valid UTF-8-encoded Unicode as well. Since ASCII bytes do not occur when encoding non-ASCII code points into UTF-8, UTF-8 is safe to use within most programming and document languages



## progressive web application

PWA is web application that could supported on any  PHP/ASP and js/HTML?CSS.  More secure.. Not support on safari. 

**Progressive Web Apps** are web apps that use emerging web browser APIs and features along with traditional progressive enhancement strategy to bring a native app-like user experience to cross-platform web applications. Progressive Web Apps are a useful design pattern, though they aren't a formalized standard. PWA can be thought of as similar to AJAX or other similar patterns that encompass a set of application attributes, including use of specific web technologies and techniques. This set of docs tells you all you need to know about them.

In order to call a Web App a PWA, technically speaking it should have the following features: [Secure contexts](https://developer.mozilla.org/en-US/docs/Web/Security/Secure_Contexts) \([**HTTPS**](https://developer.mozilla.org/en-US/docs/Glossary/HTTPS)\), one or more [Service Workers](https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API), and a [manifest file](https://developer.mozilla.org/en-US/docs/Web/Manifest).[Secure contexts](https://developer.mozilla.org/en-US/docs/Web/Security/Secure_Contexts) \([HTTPS](https://developer.mozilla.org/en-US/docs/Glossary/HTTPS)\)The web application must be served over a secure network. Being a secure site is not only a best practice, but it also establishes your web application as a trusted site especially if users need to make secure transactions. Most of the features related to a PWA such as geolocation and even service workers are available only once the app has been loaded using HTTPS.[Service workers](https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API)A service worker is a script that allows intercepting and control of how a web browser handles its network requests and asset caching. With service workers, web developers can create reliably fast web pages and offline experiences.[Manifest file](https://developer.mozilla.org/en-US/docs/Web/Manifest)A [JSON](https://developer.mozilla.org/en-US/docs/Glossary/JSON) file that controls how your app appears to the user and ensures that progressive web apps are discoverable. It describes the name of the app, the start URL, icons, and all of the other details necessary to transform the website into an app-like format.



### PWA advantages <a id="PWA_advantages"></a>

PWAs should be discoverable, installable, linkable, network independent, progressive, re-engageable, responsive, and safe. To find out more about what these mean, read [Progressive web app advantages](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Advantages).

To find out how to implement PWAs, read through our [PWA developer guide](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Developer_guide).



## [difference between 0.0.0.0, 127.0.0.1 and localhost?](https://stackoverflow.com/questions/20778771/what-is-the-difference-between-0-0-0-0-127-0-0-1-and-localhost)

`127.0.0.1` is normally the IP address assigned to the "loopback" or local-only interface. This is a "fake" network adapter that can only communicate within the same host. It's often used when you want a network-capable application to only serve clients on the same host. A process that is listening on `127.0.0.1` for connections will only receive local connections on that socket.

"localhost" is normally the hostname for the `127.0.0.1` IP address. It's usually set in `/etc/hosts` \(or the Windows equivalent named "hosts" somewhere under `%WINDIR%`\). You can use it just like any other hostname - try "ping localhost" to see how it resolves to `127.0.0.1`.

`0.0.0.0` has a couple of different meanings, but in this context, when a server is told to listen on `0.0.0.0` that means "listen on every available network interface". The loopback adapter with IP address `127.0.0.1` from the perspective of the server process looks just like any other network adapter on the machine, so a server told to listen on `0.0.0.0` will accept connections on that interface too.

## 

