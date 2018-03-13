## **Calculating with Functions**
### **5 kyu**

題目如下:

```javascript
seven(times(five())); // must return 35
four(plus(nine())); // must return 13
eight(minus(three())); // must return 5
six(dividedBy(two())); // must return 3
```

Requirements:

* There must be a function for each number from 0 ("zero") to 9 ("nine")
* There must be a function for each of the following mathematical operations: plus, minus, times, dividedBy (divided_by in Ruby)
* Each calculation consist of exactly one operation and two numbers
* The most outer function represents the left operand, the most inner function represents the right operand

>個人解法:

```javascript
function expr (number, fn) {
  if (!fn) {
    return number;
  }
  return fn(number);
}

function zero (fn) { return expr(0, fn) }
function one (fn) { return expr(1, fn) }
function two (fn) { return expr(2, fn) }
function three (fn) { return expr(3, fn) }
function four (fn) { return expr(4, fn) }
function five (fn) { return expr(5, fn) }
function six (fn) { return expr(6, fn) }
function seven (fn) { return expr(7, fn) }
function eight (fn) { return expr(8, fn) }
function nine (fn) { return expr(9, fn) }

var times = (a) => ((b) => (b * a))
var plus = (a) => ((b) => (b + a))
var minus = (a) => ((b) => (b - a))
var dividedBy = (a) => ((b) => (b / a))
```
>其他人解法:

```javascript
['zero', 'one', 'two', 'three', 'four', 'five', 'six', 'seven', 'eight', 'nine']
.forEach(function (name, n) {
  this[name] = function (f) { return f ? f(n) : n }
});

function plus(n)      { return function (a) { return a + n } }
function minus(n)     { return function (a) { return a - n } }
function times(n)     { return function (a) { return a * n } }
function dividedBy(n) { return function (a) { return a / n } }
```
