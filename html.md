# HTML

## HTML

HyperText Markup Language \(HTML\) is the standard markup language for creating web pages and web applications.

## HTML5 New Features

* Doctype
* Placeholders
* Local Storage
* Semantic elements like &lt;header&gt;, &lt;footer&gt;, &lt;article&gt;, and &lt;section&gt;
* Attributes of form elements like number, date, time, calendar, and range
* Graphic elements like &lt;svg&gt; and &lt;canvas&gt;
* Multimedia elements like &lt;audio&gt; and &lt;video&gt;



#### HTML 5 New Inline Elements <a id="mntl-sc-block_1-0-15"></a>

The new inline elements define some basic concepts and keep them semantically marked up:

* **&lt;mark&gt;** indicates content that is marked in some fashion.
* **&lt;time&gt;** indicates content that is a time or date.
* **&lt;meter&gt;** indicates content that is a fraction of a known range such as disk usage.
* **&lt;progress&gt;** indicates the progress of a task towards completion.

## Attribute vs Property

Attributes are defined on the HTML markup but properties are defined on the DOM.

## HTTP response status codes

[Information responses](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status#Information_responses) [`100 Continue`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/100)This interim response indicates that everything so far is OK and that the client should continue with the request or ignore it if it is already finished.[`101 Switching Protocol`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/101)This code is sent in response to an [`Upgrade`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Upgrade) request header by the client, and indicates the protocol the server is switching to.

### Successful responses[Section](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status#Successful_responses) <a id="Successful_responses"></a>

[`200 OK`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/200)The request has succeeded. The meaning of a success varies depending on the HTTP method:  
GET: The resource has been fetched and is transmitted in the message body.  
HEAD: The entity headers are in the message body.  
PUT or POST: The resource describing the result of the action is transmitted in the message body.

[`201 Created`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/201)The request has succeeded and a new resource has been created as a result of it. This is typically the response sent after a POST request, or after some PUT requests

Redirection messages[Section](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status#Redirection_messages)

[`300 Multiple Choice`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/300)The request has more than one possible response. The user-agent or user should choose one of them. There is no standardized way of choosing one of the responses.

Client error responses[Section](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status#Client_error_responses)

[`400 Bad Request`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/400)This response means that server could not understand the request due to invalid syntax.[`401 Unauthorized`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/401)[`402 Payment Required`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/402) [`403 Forbidden`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/403)[`404 Not Found`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/404)The server can not find requested resource. In the browser, this means the URL is not recognized. 

Server error responses[Section](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status#Server_error_responses)

[`500 Internal Server Error`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/500)The server has encountered a situation it doesn't know how to handle.  


## Cookie vs SessionStorage vs LocalStorage

All the above-mentioned technologies are key-value storage mechanisms on the client side. They are only able to store values are strings.

|  | Cookie | LocalStorage | SessionStorage |
| :--- | :--- | :--- | :--- |
| Initiator | client or server. Server can use Set-Cookie header | client | client |
| Expiry | manually set | forever | on tab close |
| Persistent across browser sessions | depends on whether expiration is set | yes | no |
| Sent to server with every HTTP request | cookies are automatically being sent via cookie header | no | no |
| Capacity | 4kb | 5mb | 5mb |
| Accessibility | any window | any window | same tab |

## Form Validation 

HTML5 introduced a new HTML validation concept called constraint validation. 

HTML constraint validation is based on: 

* HTML Input Attributes - e.g. disabled, max, required
* CSS Pseudo Selectors - e.g :disabled, :valid, :required
* DOM Properties and Methods 

## HTML data-\* attribute

The data attributes are used to store custom data private to the page or application. The data attributes give us the ability to embed custom data attributes on all HTML elements. The stored data can then be used in the page's JavaScript to create a more engaging user experience \(without any AJAX calls or sever-side database queries\). 

The data attributes consist of two parts:

* The attribute name should not contain any uppercase letters, and must be at least one character long after the prefix "data-"
* The attribute value can be any string

## HTML Semantic element

A semantic element clearly describes its meaning to both the browser and the developer. e.g. &lt;form&gt;, &lt;table&gt;, &lt;article&gt;

## HTML5 Aside element

The aside element represents a portion of the document whose content is only indirectly related to the document's main content. Asides are frequently presented as sidebars or call-out boxes.

## HTML Accessibility

* Use more semantic HTML
* Use correct headings
* Alternative text
* Declare the language and use clear language
* Write good links and link titles



