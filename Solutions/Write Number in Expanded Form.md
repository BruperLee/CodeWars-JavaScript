

## **Write Number in Expanded Form**
### **6 kyu**

題目如下:

```
expandedForm(12); // Should return '10 + 2'
expandedForm(42); // Should return '40 + 2'
expandedForm(70304); // Should return '70000 + 300 + 4'
```

>個人解法:

```javascript
function expandedForm(num) {
var list = [], numList = [];
  var i;
  while(num > 0) {
    list.push(num % 10);
    num = (num - num % 10) / 10;
  }
  
  for (i = list.length - 1; i >= 0; i--) {
    if (list[i] !== 0) {
      numList.push(list[i] * Math.pow(10, i))
    }
  }
  return numList.join(' + ');
}

```
>其他人解法:

```javascript
const expandedForm = n => n.toString()
                            .split("")
                            .reverse()
                            .map( (a, i) => a * Math.pow(10, i))
                            .filter(a => a > 0)
                            .reverse()
                            .join(" + ");
```

