# Cross-Origin Resource Sharing

## Cross-Origin Resource Sharing \(CORS\)

Cross-Origin Resource Sharing \(CORS\) is a mechanism that uses additional HTTP headers to tell a browser to let a web application running at one origin \(domain\) have permission to access selected resources from a server at a different origin. A web application executes a cross-origin HTTP request when it requests a resource that has a different origin \(domain, protocol, and port\) than its own origin. 

Browsers restrict cross-origin HTTP requests initiated from scripts. For example, `XMLHttpRequest` and the [Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API) follow the [same-origin policy](https://developer.mozilla.org/en-US/docs/Web/Security/Same-origin_policy). This means that a web application using those APIs can only request resources from the same origin the application was loaded from unless the response from other origins includes the right CORS headers.

![](../.gitbook/assets/image%20%2885%29.png)

The CORS mechanism supports secure cross-origin requests and data transfers between browsers and servers. Modern browsers use CORS in APIs such as `XMLHttpRequest` or [Fetch](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API) to mitigate the risks of cross-origin HTTP requests.

![](../.gitbook/assets/image%20%2865%29.png)



 the server responds:

```text
GET /resources/public-data/ HTTP/1.1
Host: bar.other
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.14; rv:71.0) Gecko/20100101 Firefox/71.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Connection: keep-alive
Origin: https://foo.example
```

The request header of note is [`Origin`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Origin), which shows that the invocation is coming from `https://foo.example`.

```text
HTTP/1.1 200 OK
Date: Mon, 01 Dec 2008 00:23:53 GMT
Server: Apache/2
Access-Control-Allow-Origin: *
Keep-Alive: timeout=2, max=100
Connection: Keep-Alive
Transfer-Encoding: chunked
Content-Type: application/xml
```

In response, the server sends back an [`Access-Control-Allow-Origin`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Access-Control-Allow-Origin) header. The use of the [`Origin`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Origin) header and of [`Access-Control-Allow-Origin`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Access-Control-Allow-Origin) show the access control protocol in its simplest use. In this case, the server responds with `Access-Control-Allow-Origin: *`, which means that the resource can be accessed by **any** domain. If the resource owners at `https://bar.other` wished to restrict access to the resource to requests _only_ from `https://foo.example`, they would send:

```text
Access-Control-Allow-Origin: https://foo.example
```

Now no domain other than `https://foo.example` can access the resource in a cross-site manner. To allow access to the resource, the `Access-Control-Allow-Origin` header should contain the value that was sent in the request's `Origin` header.

## The HTTP response headers

This section lists the HTTP response headers that servers send back for access control requests as defined by the Cross-Origin Resource Sharing specification. The previous section gives an overview of these in action.

#### Access-Control-Allow-Origin <a id="Access-Control-Allow-Origin"></a>

A returned resource may have one [`Access-Control-Allow-Origin`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Access-Control-Allow-Origin) header, with the following syntax:

```text
Access-Control-Allow-Origin: <origin> | *
```

`Access-Control-Allow-Origin` specifies either a single origin, which tells browsers to allow that origin to access the resource; or else — for requests **without** credentials — the "`*`" wildcard, to tell browsers to allow any origin to access the resource.

For example, to allow code from the origin `https://mozilla.org` to access the resource, you can specify:

```text
Access-Control-Allow-Origin: https://mozilla.org
Vary: Origin
```

If the server specifies a single origin \(that may dynamically change based on the requesting origin as part of a white-list\) rather than the "`*`" wildcard, then the server should also include `Origin` in the [`Vary`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Vary) response header — to indicate to clients that server responses will differ based on the value of the [`Origin`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Origin) request header.

#### Access-Control-Expose-Headers <a id="Access-Control-Expose-Headers"></a>

The [`Access-Control-Expose-Headers`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Access-Control-Expose-Headers) header lets a server whitelist headers that browsers are allowed to access.

```text
Access-Control-Expose-Headers: <header-name>[, <header-name>]*
```

For example, the following:

```text
Access-Control-Expose-Headers: X-My-Custom-Header, X-Another-Custom-Header
```

…would allow the `X-My-Custom-Header` and `X-Another-Custom-Header` headers to be exposed to the browser.

#### Access-Control-Max-Age <a id="Access-Control-Max-Age"></a>

The [`Access-Control-Max-Age`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Access-Control-Max-Age) header indicates how long the results of a preflight request can be cached. For an example of a preflight request, see the above examples.

```text
Access-Control-Max-Age: <delta-seconds>
```

The `delta-seconds` parameter indicates the number of seconds the results can be cached.

#### Access-Control-Allow-Credentials <a id="Access-Control-Allow-Credentials"></a>

The [`Access-Control-Allow-Credentials`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Access-Control-Allow-Credentials) header Indicates whether or not the response to the request can be exposed when the `credentials` flag is true. When used as part of a response to a preflight request, this indicates whether or not the actual request can be made using credentials. Note that simple `GET` requests are not preflighted, and so if a request is made for a resource with credentials, if this header is not returned with the resource, the response is ignored by the browser and not returned to web content.

```text
Access-Control-Allow-Credentials: true
```

[Credentialed requests](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS#Requests_with_credentials) are discussed above.

#### Access-Control-Allow-Methods <a id="Access-Control-Allow-Methods"></a>

The [`Access-Control-Allow-Methods`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Access-Control-Allow-Methods) header specifies the method or methods allowed when accessing the resource. This is used in response to a preflight request. The conditions under which a request is preflighted are discussed above.

```text
Access-Control-Allow-Methods: <method>[, <method>]*
```

An example of a [preflight request is given above](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS#Preflighted_requests), including an example which sends this header to the browser.

#### Access-Control-Allow-Headers <a id="Access-Control-Allow-Headers"></a>

The [`Access-Control-Allow-Headers`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Access-Control-Allow-Headers) header is used in response to a [preflight request](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS#Preflighted_requests) to indicate which HTTP headers can be used when making the actual request.

```text
Access-Control-Allow-Headers: <header-name>[, <header-name>]*


```

## The HTTP request headers

This section lists headers that clients may use when issuing HTTP requests in order to make use of the cross-origin sharing feature. Note that these headers are set for you when making invocations to servers. Developers using cross-site [`XMLHttpRequest`](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest) capability do not have to set any cross-origin sharing request headers programmatically.

#### Origin <a id="Origin"></a>

The [`Origin`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Origin) header indicates the origin of the cross-site access request or preflight request.

```text
Origin: <origin>
```

The origin is a URI indicating the server from which the request initiated. It does not include any path information, but only the server name.**Note:** The `origin` value can be `null`, or a URI.

Note that in any access control request, the [`Origin`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Origin) header is **always** sent.

#### Access-Control-Request-Method <a id="Access-Control-Request-Method"></a>

The [`Access-Control-Request-Method`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Access-Control-Request-Method) is used when issuing a preflight request to let the server know what HTTP method will be used when the actual request is made.

```text
Access-Control-Request-Method: <method>
```

Examples of this usage can be [found above.](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS#Preflighted_requests)

#### Access-Control-Request-Headers <a id="Access-Control-Request-Headers"></a>

The [`Access-Control-Request-Headers`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Access-Control-Request-Headers) header is used when issuing a preflight request to let the server know what HTTP headers will be used when the actual request is made.

```text
Access-Control-Request-Headers: <field-name>[, <field-name>]*
```

Examples of this usage can be [found above](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS#Preflighted_requests).

