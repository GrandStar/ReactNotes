# HTTP/2 & SPDY

## Goals:

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

features that distinguishes HTTP/1.1 and HTTP/2 is the binary framing layer, which can be thought of as a part of the application layer in the internet protocol stack. As opposed to HTTP/1.1, which keeps all requests and responses in plain text format, HTTP/2 uses the binary framing layer to encapsulate all messages in binary format, while still maintaining HTTP semantics, such as verbs, methods, and headers. An application level API would still create messages in the conventional HTTP formats, but the underlying layer would then convert these messages into binary. This ensures that web applications created before HTTP/2 can continue functioning as normal when interacting with the new protocol.

The conversion of messages into binary allows HTTP/2 to try new approaches to data delivery not available in HTTP/1.1, a contrast that is at the root of the practical differences between the two protocols. The next section will take a look at the delivery model of HTTP/1.1, followed by what new models are made possible by HTTP/2.

 HTTP/2 \(which was a copy of SPDY\) come from [multiplexing](https://en.wikipedia.org/wiki/Multiplexing) of requests and responses to avoid some of the [head-of-line blocking](https://en.wikipedia.org/wiki/Head-of-line_blocking) problem in HTTP 1 \(even when [HTTP pipelining](https://en.wikipedia.org/wiki/HTTP_pipelining) is used\), header [compression](https://en.wikipedia.org/wiki/Data_compression), and prioritization of requests.[\[22\]](https://en.wikipedia.org/wiki/HTTP/2#cite_note-22) However, as HTTP/2 runs on top of a single TCP connection there is still potential for head-of-line blocking to occur if TCP packets are lost or delayed in transmission.[\[23\]](https://en.wikipedia.org/wiki/HTTP/2#cite_note-23) HTTP/2 no longer supports HTTP 1.1's [chunked transfer encoding](https://en.wikipedia.org/wiki/Chunked_transfer_encoding) mechanism, as it provides its own, more efficient, mechanisms for data streaming.[\[24\]](https://en.wikipedia.org/wiki/HTTP/2#cite_note-24)

![](../.gitbook/assets/image%20%2861%29.png)

![](../.gitbook/assets/image%20%2874%29.png)

![](../.gitbook/assets/image%20%2863%29.png)

![](../.gitbook/assets/image%20%2883%29.png)

