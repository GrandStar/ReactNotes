# coding question



delete node in inkedlist

top two frequents in array

flattern object/array

#### 

```text
function flatten(arr) {
  return arr.reduce((a, b) => {
    // return Array.isArray(b) ? a.concat(flatten(b)) : a.concat(b);
    return a.concat(Array.isArray(b) ? flatten(b) : b);
  }, []);
};

// es6
const flatten = arr =>
  arr.reduce((a, b) => a.concat(Array.isArray(b) ? flatten(b) : b), []);
  
```



```text
var foo = 1;
function bar() {
	foo = 10;
	return;
	function foo() {}
}
bar();
alert(foo);
```

```text
function bar() {
    return foo;
    foo = 10;
    function foo() {}
    var foo = 11;
}
alert(typeof bar());
```

```text
function foo(){}
delete foo.length;
alert(typeof foo.length);
```

closure:

  Fibonacci closure:

  use closure to change loop / use a closure to create a private counter?

 closure in callback



Leetcode

**1  2sum**

**3 string/array  use map**[  **Longest Substring Without Repeating Characters**](https://leetcode.com/problems/longest-substring-without-repeating-characters) ****

   **use a duplicateIndex = \[\];** 

**15 3sum** [**3Sum Closes**](https://leetcode.com/problems/3sum-closest)**t**  [**3Sum With Multiplicity**](https://leetcode.com/problems/3sum-with-multiplicity)    ****

    **for loop,  left = i+ 1; right = length -1; while\(left &lt; right\)....if else**

**20**  [**Valid Parentheses**](https://leetcode.com/problems/valid-parentheses)    ****

      **push \), \], } into array, use pop\(\);**

**26**  Remove Duplicates from Sorted Array

    nums.splice\(i, 1\); i--;

**27** [**Remove Element**](https://leetcode.com/problems/remove-element)    ****

    **nums.splice\(i, 1\), i--;**

**33**[  **Search in Rotated Sorted Array**](https://leetcode.com/problems/search-in-rotated-sorted-array)   ****

    **toxic** 

**36  Valid Sudoku**

**39**  [**Combination Sum**](https://leetcode.com/problems/combination-sum) ****

       **iterative, help\(index + 1, array, target - candidates\[index\]\);**

**46** [**Permutations**](https://leetcode.com/problems/permutations)    ****

**48** [**Rotate Image**](https://leetcode.com/problems/rotate-image)    ****

**49**

**73** [**Set Matrix Zeroes**](https://leetcode.com/problems/set-matrix-zeroes) ****

**80** [**Remove Duplicates from Sorted Array II**](https://leetcode.com/problems/remove-duplicates-from-sorted-array-ii)   ****

   **splice\(\), O\(n\)**

**88** [**Merge Sorted Array**](https://leetcode.com/problems/merge-sorted-array)    ****

**94** [**Binary Tree Inorder Traversal**](https://leetcode.com/problems/binary-tree-inorder-traversal)   ****

**102** [**Binary Tree Level Order Traversal**](https://leetcode.com/problems/binary-tree-level-order-traversal)    ****

**121** array / dp  ****[**Best Time to Buy and Sell Stock**](https://leetcode.com/problems/best-time-to-buy-and-sell-stock)   ****

        **tempmin, tempmax, res. for loop ON/// try to use reduce**

```text
    let minPrice = +Infinity;
```

**\*\*\*\*\* 125 Valid Palindrom** 

let str = s.replace\(/\W/g, ''\).toLowerCase\(\);

**144** [**Binary Tree Preorder Traversal**](https://leetcode.com/problems/binary-tree-preorder-traversal)    ****

**151** [**Reverse Words in a String**](https://leetcode.com/problems/reverse-words-in-a-string)   ****

**155** [**Min Stack**](https://leetcode.com/problems/min-stack)   ****

**192** [**Word Frequency**](https://leetcode.com/problems/word-frequency)    ****

**203** [**Remove Linked List Elements**](https://leetcode.com/problems/remove-linked-list-elements) ****

**204**[ **Count Primes**](https://leetcode.com/problems/count-primes)\*\*\*\*

**206** [**Reverse Linked List**](https://leetcode.com/problems/reverse-linked-list)  ****

**238** [**Product of Array Except Self**](https://leetcode.com/problems/product-of-array-except-self)    ****

**268** [**Missing Number**](https://leetcode.com/problems/missing-number)  ****

       **use sum, reduce get array sum, diff.**

**283** [**Move Zeroes**](https://leetcode.com/problems/move-zeroes)    ****

**from back to front.**

```text
var moveZeroes = function(nums) {       
    for(var i = nums.length;i--;){
        if(nums[i]===0){
            nums.splice(i,1)
            nums.push(0);
        }
    }
};
```

**300**  [**Longest Increasing Subsequence**](https://leetcode.com/problems/longest-increasing-subsequence)\*\*\*\*

**316**  [**Remove Duplicate Letters**](https://leetcode.com/problems/remove-duplicate-letters) ****

**349** [ **Intersection of Two Arrays**](https://leetcode.com/problems/intersection-of-two-arrays)    ****

**387 String  First Unique Character in a String**

      **2 pass;**

**394** [ **Decode String**](https://leetcode.com/problems/decode-string)   ****

**509 Fibonacci closure**

**819** [Most Common Word](https://leetcode.com/problems/most-common-word)    

\*\*\*\*

\*\*\*\*

\*\*\*\*

## Use array/Object for any question.

string =  array.join\(""\);

no need queue, stack, map

