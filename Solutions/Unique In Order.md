## **Unique In Order**
### **6 kyu**

題目如下:

Implement the function unique_in_order which takes as argument a sequence and returns a list of items without any elements with the same value next to each other and preserving the original order of elements.

For example:

```
uniqueInOrder('AAAABBBCCDAABBB') == ['A', 'B', 'C', 'D', 'A', 'B']
uniqueInOrder('ABBCcAD')         == ['A', 'B', 'C', 'c', 'A', 'D']
uniqueInOrder([1,2,2,3,3])       == [1,2,3]
```

>個人解法:

```javascript
var uniqueInOrder=function(iterable){
  //your code here - remember iterable can be a string or an array
  var temp, result = [];
  
  for (var i = 0; i < iterable.length; i++) {
    if (temp !== iterable[i]) {
      temp = iterable[i];  
      result.push(temp);
    }
  }
  return result;
}
```
>其他人解法:

```javascript
var uniqueInOrder=function(iterable){
  return Array.prototype.reduce.call(iterable, function(a,b) { if (a[a.length-1] !== b) a.push(b); return a; }, []);
}
```

>其他人解法:

```javascript
var uniqueInOrder=function(iterable){
  return Array.prototype.filter.call(iterable, function(current, index){ return iterable[index - 1] !== current})
}
```
