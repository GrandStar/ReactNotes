---
description: 'https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers'
---

# HTTP Header

Cache Header

{% embed url="https://www.keycdn.com/blog/http-cache-headers" %}

[https://devcenter.heroku.com/articles/increasing-application-performance-with-http-cache-headers](https://devcenter.heroku.com/articles/increasing-application-performance-with-http-cache-headers)

![](../.gitbook/assets/image%20%2873%29.png)

Caches work with content mainly through freshness and validation. A fresh representation is available instantly from a cache while a validated representation rarely sends the entire representation again if it hasn't changed. In cases where there is no validator present \(e.g. `ETag` or `Last-Modified` header\), and a lack of explicit freshness info, it will usually \(but not always\) be considered uncacheable. Let's shift our focus to the kind of headers you should be concerned about.



#### Extension `Cache-Control` directives[\#](https://www.keycdn.com/blog/http-cache-headers#5-extension-cache-control-directives) <a id="5-extension-cache-control-directives"></a>

Apart from the well-known `Cache-Control` directives outlined in the first section of this article, there also exists other directives which can be used as extensions to `Cache-Control` resulting in a better user experience for your visitors.



```text
Cache-Control: max-age=<seconds>
Cache-Control: max-stale[=<seconds>]
Cache-Control: min-fresh=<seconds>
Cache-control: no-cache 
Cache-control: no-store
Cache-control: no-transform
Cache-control: only-if-cached
```

**immutable\#**

No conditional revalidation will be triggered even if the user explicitly refreshes a page. The immutable directive tells the client that the response body will not change over time, therefore, there is no need to check for updates as long as it is unexpired.

**stale-while-revalidate\#**

The `stale-while-revalidate` directive allows for a stale asset to be served while it is revalidated in the background.

