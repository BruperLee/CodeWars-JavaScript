## **Largest 5 digit number in a series**
### **5 kyu**

題目如下:

In the following 10 digit number:

```
1234567890
```
`67890` is the greatest sequence of 5 consecutive digits..

>個人解法:

```javascript
function solution(digits){
  let largest = '';
  let s = String(digits);
  
  for (var i = 5; i <= s.length; i++) {
    largest = s.slice(i - 5, i) > largest ? s.slice(i - 5, i) : largest;
  }
  
  return Number.parseInt(largest, 10);
}
```
>其他人解法:

```javascript
function solution(digits){
  if (digits.length <= 5) return Number(digits);
  return Math.max(Number(digits.substr(0, 5)), solution(digits.substr(1)));
}
```
