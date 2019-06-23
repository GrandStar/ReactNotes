---
description: 'Array, String, Object'
---

# function API

## Array 

InPlace:push\(\)/pop\(\), shift\(\)/unshift\(\), splice\(\), copyWithin\(\), fill\(\), reverse\(\), sort\(\)  


ReturnNew: concat\(\), slice\(\)  


Matching: indexOf\(\), lastIndexOf\(\), find\(\), findIndex\(\), some\(\), every\(\), join\(\)

**traverse forEach** executes the provided callback once for each element present in the array in ascending order.

```text
fruits.forEach(function (item, index, array) {
    console.log(item, index);
});
```

•Does not make a copy of the array before iterating.

```text
split
var myArray = myData.split(',');
var myNewString = myArray.join(',');
myNewString;
```

 push\(\): add to last.

pop\(\): delete last and return this one.



[`toString()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/toString)

1. ```text
   var dogNames = ["Rocket","Flash","Bella","Slugger"];
   dogNames.toString(); //Rocket,Flash,Bella,Slugger
   ```



```text
var myArray = ['Manchester', 'Leeds', 'Carlisle'];
myArray.push('Cardiff');
myArray.pop();
pop() delete last one
var removedItem = myArray.pop();
```

[`unshift()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/unshift)  [`shift()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/shift) `100% like push and pop, only on the begining`

`unshift(): add to head.`

```text
myArray.unshift('Edinburgh');
var removedItem = myArray.shift();
```



```text
.indexOf(element) return the index
```

Splice: delete some elements:

```text
array.splice(start[, deleteCount[, item1[, item2[, ...]]]])
start position, delete number, items to add.from start
return the [] that deleted.
```

```text
var removedItem = fruits.splice(pos, 1); 
```

.fill\(\) fill all indexes.

[`.concat()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/concat) ``

[`Array.prototype.includes()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/includes)

[`Array.prototype.join()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/join)   `concat and return a new String`

[`Array.prototype.slice()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/slice)  `get some return a new array`

[`Array.prototype.toString()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/toString)

[`Array.prototype.lastIndexOf()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/lastIndexOf) `return the last index..`



Traverse:

[`Array.prototype.forEach()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)

[`Array.prototype.map()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/map)

[`Array.prototype.reduce()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce)

[`Array.prototype.some()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/some)  `as least one or return false;`



## Object



•**map** transforms the elements in the array

•Based on a function you give

•Return a copy and doesn’t modify the input array

•When the function you provide gets called, it gets called for each element with three arguments: the element itself, the index of the element, and the array itself \(which is seldom useful\).

•**filter** removes unwanted things from an input array.

•Based on a function you give

•Return a copy and doesn’t modify the input array

•map and filter often are used together

### Reduce\(\)

array.reduce\(\(accumulator, currentValue, currentIndex, sourceArray\) =&gt; {  }\)

```
arr.reduce(callback(accumulator, currentValue[, index[, array]])[, initialValue])
```



## String



## typeof

**typeof null = objec**

| **Type** | result |
| :--- | :--- |
| Null | `"object"`（见下文） |
| Boolean | `"boolean"` |
| Number | `"number"` |
| String | `"string"` |
| Symbol （ECMAScript 6 新增） | `"symbol"` |
| 宿主对象（由JS环境提供） | _Implementation-dependent_ |
| 函数对象（\[\[Call\]\] 在ECMA-262条款中实现了） | `"function"` |
| 任何其他对象 | `"object"` |

New

```text
var str = new String('String');
var num = new Number(100);
typeof str; // It will return 'object'
typeof num; // It will return 'object'
```

