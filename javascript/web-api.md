# Web API



A Web API is a developer's dream.

* It can extend the functionality of the browser
* It can greatly simplify complex functions
* It can provide easy syntax to complex code

**Browser APIs**

All browsers have a set of built-in Web APIs to support complex operations, and to help accessing data.

For example, the Geolocation API can return the coordinates of where the browser is located.

**Example**

Get the latitude and longitude of the user's position

```javascript
var x = document.getElementById("demo");

function getLocation() {
  if (navigator.geolocation) {
    navigator.geolocation.getCurrentPosition(showPosition);
  } else {
    x.innerHTML = "Geolocation is not supported by this browser.";
  }
}

function showPosition(position) {
  x.innerHTML = "Latitude: " + position.coords.latitude +
  "<br>Longitude: " + position.coords.longitude;
}

```

## Web History API

### The History back\(\) Method

The back\(\) method loads the previous URL in the windows.history list.

It is the same as clicking the "back arrow" in your browser.

```javascript
<button onclick="myFunction()">Go Back</button>
<script>
function myFunction() {
  window.history.back();
}
</script>
```

### The History go\(\) Method

The go\(\) method loads a specific URL from the history list:

```javascript
<button onclick="myFunction()">Go Back 2 Pages</button>

<script>
function myFunction() {
  window.history.go(-2);
}
</script>
```

| [back\(\)](https://www.w3schools.com/jsref/met_his_back.asp) | Loads the previous URL in the history list |
| :--- | :--- |
| [forward\(\)](https://www.w3schools.com/jsref/met_his_forward.asp) | Loads the next URL in the history list |
| [go\(\)](https://www.w3schools.com/jsref/met_his_go.asp) | Loads a specific URL from the history list |

## Web Storage API

The Web Storage API is a simple syntax for storing and retrieving data in the browser. It is very easy to use:

localStorage.setItem\("name", "John Doe"\);

 localStorage.getItem\("name"\);

### The localStorage Object

The localStorage object provides access to a local storage for a particular Web Site. It allows you to store, read, add, modify, and delete data items for that domain.

The data is stored with no expiration date, and will not be deleted when the browser is closed.

The data will be available for days, weeks, and years.

### The setItem\(\) Method

The localStorage.setItem\(\) method stores a data item in a storage.

It takes a name and a value as parameters:

#### Example

localStorage.setItem\("name", "John Doe"\);

### The getItem\(\) Method

The localStorage.getItem\(\) method retrieves a data item from the storage.

It takes a name as parameter:

#### Example

localStorage.getItem\("name"\);

### The sessionStorage Object

The sessionStorage object is identical to the localStorage object.

The difference is that the sessionStorage object stores data for one session.

The data is deleted when the browser is closed.

#### Example

sessionStorage.getItem\("name"\);

### The setItem\(\) Method

The sessionStorage.setItem\(\) method stores a data item in a storage.

It takes a name and a value as parameters:

#### Example

sessionStorage.setItem\("name", "John Doe"\);

### The getItem\(\) Method

The sessionStorage.getItem\(\) method retrieves a data item from the storage.

It takes a name as parameter:

#### Example

sessionStorage.getItem\("name"\);



### Storage Object Properties and Methods

| Property/Method | Description |
| :--- | :--- |
| [key\(_n_\)](https://www.w3schools.com/jsref/met_storage_key.asp) | Returns the name of the _n_th key in the storage |
| [length](https://www.w3schools.com/jsref/prop_storage_length.asp) | Returns the number of data items stored in the Storage object |
| [getItem\(_keyname_\)](https://www.w3schools.com/jsref/met_storage_getitem.asp) | Returns the value of the specified key name |
| [setItem\(_keyname_, _value_\)](https://www.w3schools.com/jsref/met_storage_setitem.asp) | Adds that key to the storage, or update that key's value if it already exists |
| [removeItem\(_keyname_\)](https://www.w3schools.com/jsref/met_storage_removeitem.asp) | Removes that key from the storage |
| [clear\(\)](https://www.w3schools.com/jsref/met_storage_clear.asp) | Empty all key out of the storage |

### Related Pages for Web Storage API

| Property | Description |
| :--- | :--- |
| [window.localStorage](https://www.w3schools.com/jsref/prop_win_localstorage.asp) | Allows to save key/value pairs in a web browser. Stores the data with no expiration date |
| [window.sessionStorage](https://www.w3schools.com/jsref/prop_win_sessionstorage.asp) | Allows to save key/value pairs in a web browser. Stores the data for one session |

## Web Geolocation API

The `getCurrentPosition()` method is used to return the user's position.

The example below returns the latitude and longitude of the user's position:

```javascript
<script>
var x = document.getElementById("demo");
function getLocation() {
  if (navigator.geolocation) {
    navigator.geolocation.getCurrentPosition(showPosition);
  } else {
    x.innerHTML = "Geolocation is not supported by this browser.";
  }
}

function showPosition(position) {
  x.innerHTML = "Latitude: " + position.coords.latitude +
  "<br>Longitude: " + position.coords.longitude;
}
</script>

```

### Displaying the Result in a Map

To display the result in a map, you need access to a map service, like Google Maps.

In the example below, the returned latitude and longitude is used to show the location in a Google Map \(using a static image\):

#### Example

```javascript
function showPosition(position) {
  var latlon = position.coords.latitude + "," + position.coords.longitude;

  var img_url = "https://maps.googleapis.com/maps/api/staticmap?center=
  "+latlon+"&zoom=14&size=400x300&sensor=false&key=YOUR_KEY";

  document.getElementById("mapholder").innerHTML = "<img src='"+img_url+"'>";
}
```

### Location-specific Information

This page has demonstrated how to show a user's position on a map.

Geolocation is also very useful for location-specific information, like:

* Up-to-date local information
* Showing Points-of-interest near the user
* Turn-by-turn navigation \(GPS\)





