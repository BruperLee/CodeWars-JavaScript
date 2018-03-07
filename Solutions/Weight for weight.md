

## **Weight for weight**
### **5 kyu**

題目如下:

My friend John and I are members of the "Fat to Fit Club (FFC)". John is worried because each month a list with the weights of members is published and each month he is the last on the list which means he is the heaviest.

I am the one who establishes the list so I told him: "Don't worry any more, I will modify the order of the list". It was decided to attribute a "weight" to numbers. The weight of a number will be from now on the sum of its digits.

For example 99 will have "weight" 18, 100 will have "weight" 1 so in the list 100 will come before 99. Given a string with the weights of FFC members in normal order can you give this string ordered by "weights" of these numbers?

For example:

"56 65 74 100 99 68 86 180 90" ordered by numbers weights becomes: "100 180 90 56 65 74 68 86 99"

When two numbers have the same "weight", let us class them as if they were strings and not numbers: 100 is before 180 because its "weight" (1) is less than the one of 180 (9) and 180 is before 90 since, having the same "weight" (9) it comes before as a string.

```
orderWeight("103 123 4444 99 2000")    // "2000 103 123 4444 99"
orderWeight("2000 10003 1234000 44444444 9999 11 11 22 123")   //"11 11 2000 10003 22 123 1234000 44444444 9999"
```

>個人解法:

```javascript
function orderWeight(string) {
  let stringList = string.split(' ');

  const sum = (str) => {
    return str.split('').reduce((total, val) => {
      return total += parseInt(val);
    }, 0);
  }

  stringList.sort((a, b) => {
    return sum(a) === sum(b) ? (a < b ? -1 : 1) : sum(a) - sum(b);
  });
    
  return stringList.join(' ');
}

```
>其他人解法:

```javascript
function orderWeight(strng) {
  return strng
    .split(" ")
    .map(function(v) {  
      return {
        val: v,
        key: v.split("").reduce(function(prev, curr) {
          return parseInt(prev) + parseInt(curr);
        }, 0)
      };
    })
    .sort(function(a, b) {
      return a.key == b.key 
        ? a.val.localeCompare(b.val)
        : (a.key - b.key);
    })
    .map(function(v) {
      return v.val;
    })
    .join(" ");
}
```

>其他人解法:

```javascript
function orderWeight(strng) {
 const sum = (str)=>str.split('').reduce((sum,el)=>(sum+(+el)),0);
  function comp(a,b){
    let sumA = sum(a);
    let sumB = sum(b);
    return sumA === sumB ? a.localeCompare(b) : sumA - sumB;
   };
 return strng.split(' ').sort(comp).join(' ');
}
```
