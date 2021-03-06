---
description: 'https://developer.mozilla.org/en-US/docs/Web'
---

# WEB Network HTTP etc

## OAuth, OpenID Connect, and SAML

**OAuth** 

an application can take actions or access resources from a server on behalf of the user, without them having to share their credentials. It does this by allowing the [identity provider \(IdP\)](https://www.okta.com/identity-101/why-your-company-needs-an-identity-provider/) to issue tokens to third-party applications with the user’s approval.

op**enid**

OpenID Connect 1.0 is a simple identity layer on top of the OAuth 2.0 protocol. It allows Clients to verify the identity of the End-User based on the authentication performed by an Authorization Server, as well as to obtain basic profile information about the End-User in an interoperable and REST-like manner.

**saml**

enables you to log into your corporate intranet or IdP and then access numerous additional services, such as Salesforce, Box, or Workday, without having to re-enter your credentials. SAML is an XML-based standard for exchanging authentication and authorization data between IdPs and service providers to verify the user’s identity and permissions, then grant or deny their access to services.



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

Cross-Origin Resource Sharing \([CORS](https://developer.mozilla.org/en-US/docs/Glossary/CORS)\) is a mechanism that uses additional [HTTP](https://developer.mozilla.org/en-US/docs/Glossary/HTTP)headers to tell a browser to let a web application running at one origin \(domain\) have permission to access selected resources from a server at a different origin. A web application executes a **cross-origin HTTP request** when it requests a resource that has a different origin \(domain, protocol, and port\) than its own origin.

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

![](.gitbook/assets/image%20%2828%29.png)

An example of a cross-origin request: The frontend JavaScript code for a web application served from `http://domain-a.com` uses [`XMLHttpRequest`](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest) to make a request for `http://api.domain-b.com/data.json`.

![](.gitbook/assets/image%20%2832%29.png)

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

![](.gitbook/assets/image%20%2874%29.png)

Pv6 uses a 128-bit address, theoretically allowing 2^128 addresses.

The two protocols are not designed to be [interoperable](https://en.wikipedia.org/wiki/Interoperable)

![Glossary of terms used for IPv6 addresses.](.gitbook/assets/image%20%2872%29.png)

![](.gitbook/assets/image%20%2868%29.png)

### Comparison with IPv4:

#### Larger address space

#### Multicasting

![](.gitbook/assets/image%20%2862%29.png)

[Multicasting](https://en.wikipedia.org/wiki/Multicast), the transmission of a packet to multiple destinations in a single send operation, is part of the base specification in IPv6.

#### Stateless address autoconfiguration \(SLAAC\) SLAAC

IPv6 hosts configure themselves automatically. Every interface has a self-generated link-local address and, when connected to a network, conflict resolution is performed and routers provide network prefixes via router advertisements.

#### IPsec

The IPsec Authentication Header \(AH\) and the Encapsulating Security Payload header \(ESP\) are implemented as IPv6 extension headers



## HTTP/2 <a id="firstHeading"></a>

#### Goals:

* Create a negotiation mechanism that allows clients and servers to elect to use HTTP 1.1, 2.0, or potentially other non-HTTP protocols.
* Maintain high-level compatibility with HTTP 1.1 \(for example with [methods](https://en.wikipedia.org/wiki/HTTP_method), [status codes](https://en.wikipedia.org/wiki/HTTP_status_code), [URIs](https://en.wikipedia.org/wiki/URI), and most [header fields](https://en.wikipedia.org/wiki/List_of_HTTP_header_fields)\).
* Decrease [latency](https://en.wikipedia.org/wiki/Latency_%28engineering%29) to improve page load speed in [web browsers](https://en.wikipedia.org/wiki/Web_browser) by considering:
  * [data compression](https://en.wikipedia.org/wiki/Data_compression) of [HTTP headers](https://en.wikipedia.org/wiki/HTTP_header)
  * [HTTP/2 Server Push](https://en.wikipedia.org/wiki/HTTP/2_Server_Push)
  * [pipelining](https://en.wikipedia.org/wiki/HTTP_pipelining) of requests
  * fixing the [head-of-line blocking](https://en.wikipedia.org/wiki/Head-of-line_blocking) problem in HTTP 1.x
  * [multiplexing](https://en.wikipedia.org/wiki/Multiplexing) multiple requests over a single [TCP](https://en.wikipedia.org/wiki/Transmission_Control_Protocol) connection
* Support common existing use cases of HTTP, such as desktop web browsers, mobile web browsers, web APIs, [web servers](https://en.wikipedia.org/wiki/Web_server) at various scales, [proxy servers](https://en.wikipedia.org/wiki/Proxy_server), [reverse proxy](https://en.wikipedia.org/wiki/Reverse_proxy) servers, [firewalls](https://en.wikipedia.org/wiki/Firewall_%28computing%29), and [content delivery networks](https://en.wikipedia.org/wiki/Content_delivery_network).

Hashing Token.  Web socket Token

bearer token

[OAuth 2.0 Bearer Token Usage](https://oauth.net/2/bearer-tokens/)

OAuth2 `accessCode`

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

![](.gitbook/assets/image%20%2857%29.png)

The `Content-Type` header illustrates the value of applying JavaScript to validate headers. If your application expects to receive a [JSON](http://www.json.org/) \(JavaScript Object Notation\) response body, then from the point of view of your application, this API is down if the response’s `Content-Type` header doesn’t include `application/json`.

#### Timing-Out Slow-Performing API Requests

#### Time-outs with Respect to Data Size

#### Using JavaScript to Validate API Response Bodies

#### Using Regular Expressions and JavaScript to Validate API Responses



[query-auth](https://github.com/jeremykendall/query-auth)

Websocket

![](.gitbook/assets/image%20%2856%29.png)

![](.gitbook/assets/image%20%2858%29.png)

{% embed url="https://www.ruanyifeng.com/blog/2017/05/websocket.html" %}

##  microservice

A microservice architecture involves many services that are each responsible for a small amount of functionality.

These services must communicate with each other over a network; since such communication would not be necessary in other architectures \(e.g. monolithic\), lower network latency is **not** a claimed benefit of microservice architecture.

Since the services are mostly self-contained, there’s less coupling and improved modularity between the various services.

By distributing functionality among multiple services, failure in part of the system does not necessarily result in failure of the entire system; this graceful degradation can lead to improved resiliency against failures. Furthermore, a microservice architecture makes it easier to introduce redundancy for critical components.

Finally, since it’s easier for developers to work on a particular service without affecting the rest of the system, it’s also easier to achieve continuous delivery.

