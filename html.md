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



## Cross-Origin Resource Sharing \([CORS](https://developer.mozilla.org/en-US/docs/Glossary/CORS)\) 

Cross-Origin Resource Sharing \([CORS](https://developer.mozilla.org/en-US/docs/Glossary/CORS)\) is a mechanism that uses additional [HTTP](https://developer.mozilla.org/en-US/docs/Glossary/HTTP)headers to tell a browser to let a web application running at one origin \(domain\) have permission to access selected resources from a server at a different origin. A web application executes a **cross-origin HTTP request** when it requests a resource that has a different origin \(domain, protocol, and port\) than its own origin.

## 

