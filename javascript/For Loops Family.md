For Loops Family in Javascript
===============================
There're three types of For Loops in Javascript.
### 1. For Loop
```javascript
const days = ['sunday', 'monday', 'tuesday', 'wednesday', 'thursday', 'friday', 'saturday'];

for(let i = 0; i < days.length; i++) {
  console.log(days[i]);
}
```
For Loop have to keep **the counter** and **exit condition**.  

### 2. For ...in Loop
```javascript
const days = ['sunday', 'monday', 'tuesday', 'wednesday', 'thursday', 'friday', 'saturday'];

for(const index in days) {
  console.log(days[index]);
}
```
For ...in loop doesn't have a counting logic and exit condition, but still have an **index**.  
Also, it also contains other properties in loop such as additional method in prototype.
```javascript
Array.prototype.decimalfy = function() {
  for (let i = 0; i < this.length; i++) {
    this[i] = this[i].toFixed(2);
  }
};

const digits = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];

for (const index in digits) {
  console.log(digits[index]);
}

/* Prints:
0
1 
2
...
9   
function() {
 for (let i = 0; i < this.length; i++) {
  this[i] = this[i].toFixed(2);  
 }
} 
*/
```
  
### 3. For ...of Loop
For ...of Loop is from ECMAScript6, and it is the best way of for loop.   
No **index** and it only loop over the values in the object, so don't have to worry about adding new properties.
```javascript
const days = ['sunday', 'monday', 'tuesday', 'wednesday', 'thursday', 'friday', 'saturday'];

for(const day of days) {
  console.log(day);
}
```
