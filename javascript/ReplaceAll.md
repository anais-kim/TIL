replaceAll() in Javascript
========================================

---------------------
### 1. No replace all method in Javascript

In javascript, there's no **String.replaceAll()** method.   
There's only String.replace() method, and it only replace the first value of the given String.
```javascript
const original = "I am carol kim. You can call me just carol.";
const replaced = original.replace('carol', 'anais');
console.log(replaced);
```
> **Results:** I am anais kim. You can call me just carol.

-------------------
### 2. Use regular expression to replace all

We can use regular expression to replace all values in given String.  
```javascript
const original = "I am carol kim. You can call me just carol.";
const replaced = original.replace(/carol/g, 'anais');
console.log(replaced);
```
> **Results:** I am anais kim. You can call me just anais.  

* for more information:   
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/replace

----------------------
### 3. Make replace all method.

We can make replaceAll() method using prototype.
```javascript
String.prototype.replaceAll = function(searchStr, replaceStr) {
    return this.split(searchStr).join(replaceStr);
}

const original = "I am carol kim. You can call me just carol.";
const replaced = original.replaceAll('carol', 'anais');
console.log(replaced);
```
> **Results:** I am anais kim. You can call me just anais.  
It's quite simple. Using split() and join() method's separator, we can replace the value what we want.
