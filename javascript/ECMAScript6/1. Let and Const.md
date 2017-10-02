ECMAScript 6 (ES6)
====================
* referenced by udacity course: https://classroom.udacity.com/courses/ud356

## 1. Syntax
### 1-1. Let and Const
There are three ways to declare variablers in Javascript: **var, let, const**.  
**let** and **const** are from ECMAScript 6, and they became because there are some problems using **var**.
#### 1-1-1. Problems of using Var: Hoisting
```javascript
function getClothing(isCold) {
  if(isCode) {
    var freezing = "Let's take a coat";
  } else {
    var hot = "Let's taka a shorts";
  }
  console.log(freezing);
}
```
if we run **getClothing(false)**, console result is **undefined**, not 'ReferencedError'.
That's because of function hoisting. Before javascript executed, all variables are **hoisted** which means they're raised on top of the function scope.
```javascript
// what really happens in browser.
function getClothing(isCold) {
  var freezing, hot;
  if(isCode) {
    freezing = "Let's take a coat";
  } else {
    hot = "Let's taka a shorts";
  }
  console.log(freezing);
}
```
### 1-1-2. Let and Const
Let and Const can solve the problem. They're scoped in **block**, not function.  
When we use 'var', it can only be scoped in function or global, not block.  
but when we use 'let' and 'const', they are scoped in block, so you can use them safely.
```javascript
function getClothing(isCold) {
  if(isCode) {
    let freezing = "Let's take a coat";
  } else {
    let hot = "Let's taka a shorts";
  }
  console.log(freezing);
}
```
When we run 'getClothing(false)', console resulst if 'ReferencedError: freezing is not defined.'

### 1.1.3. When we use Let, Const, Var?
* use let when you plan to reassign new values to a variable.  
 : because let can be reassigned.
 
* use const when you don't plan to reassign new values to a variable.  
 : because const can't be reassigned.
 
* use var when you want to use variable globally.  
 : however, it is often bad practice.  
 
So... let's use let and const instead of var :) 
