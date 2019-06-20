# function API

## Array 

InPlace:push\(\)/pop\(\), shift\(\)/unshift\(\), splice\(\), copyWithin\(\), fill\(\), reverse\(\), sort\(\)  


ReturnNew: concat\(\), slice\(\)  


Matching: indexOf\(\), lastIndexOf\(\), find\(\), findIndex\(\), some\(\), every\(\), join\(\)

**forEach** executes the provided callback once for each element present in the array in ascending order.

•Does not make a copy of the array before iterating.

•**map** transforms the elements in the array

•Based on a function you give

•Return a copy and doesn’t modify the input array

•When the function you provide gets called, it gets called for each element with three arguments: the element itself, the index of the element, and the array itself \(which is seldom useful\).

•**filter** removes unwanted things from an input array.

•Based on a function you give

•Return a copy and doesn’t modify the input array

•map and filter often are used together

