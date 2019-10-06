# Reference VS Copy

## Data Type

자바스크립트의 데이터 타입은 원시 타입과 참조 타입으로 나뉜다.  
원시 타입에는 Number, String, Boolean, 특수값(undefined, null), Symbol이 있다.  
나머지는 모두 참조 타입이다. Object, Array, Function 등.  

- 원시 타입은 값을 복사한다.

```javascript
let num = 10;
let num2 = num;
num = 20;
console.log(num, num2); // 20 10
```

- 참조 타입은 참조를 복사한다. (Reference)

```javascript
let obj = {a: 0};
let obj2 = obj;
obj.a = 1;
console.log(obj, obj2); // {a: 1} {a: 1}
```

---

## How to Copy Array
	
1.  Array.prototype.slice()
```javascript
let array = [1, 2, 3];
let array2 = array.slice();
array.push(4);

console.log(array); // [1, 2, 3, 4]
console.log(array2); // [1, 2, 3]
```

2. Array.prototype.concat()
```javascript
let array = [1, 2, 3];
let array2 = new Array().concat(array);
array.push(4);

console.log(array); // [1, 2, 3, 4]
console.log(array2); // [1, 2, 3]
```

3.  ES6 Spread
```javascript
let array = [1, 2, 3];
let array2 = [...array];
array.push(4);

console.log(array); // [1, 2, 3, 4]
console.log(array2); // [1, 2, 3]
```

---

## How to Copy Object

1. Object.assign()
```javascript
let obj = {a: 0};
let obj2 = Object.assign({}, obj);
obj.a = 1;

console.log(obj); // {a: 1}
console.log(obj2); // {a: 0}
```

2. ES6 Spread (ECMA Script 2018에서 추가)
```javascript
let obj = {a: 0};
let obj2 = {...obj}
obj.a = 1;

console.log(obj); // {a: 1}
console.log(obj2); // {a: 0}
```

---

## Trouble with Deep Copy

위의 방법들은 모두 Deep Copy를 지원하지 않는다.

```javascript
let array = [{a: 0}, {a: 1}];
let array2 = [...array];
array[0].a = 1;

console.log(array); // [{a: 1}, {a: 1}]
console.log(array2); // [{a: 1}, {a: 1}]
```

```javascript
let obj = {a: 0, b: {c: 0}};
let obj2 = Object.assign(obj);
obj.b.c = 1;

console.log(obj); // {a: 0, b: {c: 1}}
console.log(obj2); // {a: 0, b: {c: 1}}
```

- **lodash**에서 _.cloneDeep()을 제공한다. _.clone()을 재귀적으로 호출하는 함수이다.  
[https://lodash.com/docs/4.17.15#cloneDeep](https://lodash.com/docs/4.17.15#cloneDeep)
