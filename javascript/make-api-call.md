# make API call

## How to make HTTP request

* AJAX
* jQuery 
* Fetch
* Axios



## Fetch 

A Fetch API provides a fetch method defined on a window object, which you can use to perform requests and sent it to the server. This method returns a Promise that you can use to retrieve the response of the request.



```text
fetch('https://api.mydomain.com').
then(response => response.json()).
then(data => this.setState({ data }));
```



```text
fetch('http://example.com/movies.json')
  .then(function(response) {
    return response.json();
  })
  .then(function(myJson) {
    console.log(myJson);
  });
```

## Fetching data from the server

![A basic web app data flow architecture](https://mdn.mozillademos.org/files/6479/web-app-architecture@2x.png)

```text
fetch("/add", {
        method: "POST",
        headers: {
            Accept: "application/json",
            "Content-Type": "application/json"
        },
        body: JSON.stringify({
            a: parseInt(a),
            b: parseInt(b)
        })
    })
    .then(res => res.json())
    .then(data => {
        const {
            result
        } = data;
        document.querySelector(
            ".result"
        ).innerText = `The sum is: ${result}`;
    })
    .catch(err => console.log(err));
```

## 

## AJAX



```text
function reqListener () {
  console.log(this.responseText);
}

var oReq = new XMLHttpRequest();
oReq.addEventListener("load", reqListener);
oReq.open("GET", "http://www.example.org/example.txt");
oReq.send();
```

## 

## Axios

```text
axios.post('/user', {
    firstName: 'Fred',
    lastName: 'Flintstone'
  })
  .then(function (response) {
    console.log(response);
  })
  .catch(function (error) {
    console.log(error);
  });
```

##  

