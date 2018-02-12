## **Consecutive strings**
### **6 kyu**

題目如下:

You are given an array strarr of strings and an integer k. Your task is to return the first longest string consisting of k consecutive strings taken in the array.

Example: longest_consec(["zone", "abigail", "theta", "form", "libe", "zas", "theta", "abigail"], 2) --> "abigailtheta"

n being the length of the string array, if n = 0 or k > n or k <= 0 return "".

>個人解法:

```javascript
function longestConsec(strarr, k) {
    var i, j, temp = "", result = "";
    for (i = 0; i < strarr.length; i++) {
    	temp = strarr.slice(i, k + i).join('');
      
      if (temp.length > result.length) {
        result = temp;
      }
    }
    
    return result;
}
```
>其他人解法:

```javascript
function longestConsec(strarr, k) {
  if (k <= 0 || k > strarr.length) {
    return '';
  }
  
  return strarr.reduce((long, item, i) => {
    const currString = strarr.slice(i, i + k).join('');
    return (currString.length > long.length)
      ? currString
      : long;
  }, '');
}
```
