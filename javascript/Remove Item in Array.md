### Remove Item in Array

1. Array.prototype.filter()

```javascript
const comments = [
{ text: 'Love this!', id:  523423 },
{ text: 'Super good', id:  823423 },
{ text: 'You are the best', id:  2039842 },
{ text: 'Ramen is my fav food ever', id:  123523 },
{ text: 'Nice Nice Nice!', id:  542328 }
];

const newComments = comments.filter(comment => comment.id !== 823423);
console.log(newComments); // (4) [{…}, {…}, {…}, {…}]
```

---

2. Array.prototype.splice()
- splice()는 기존 배열을 변경 시키고 추출한 값을 리턴한다.
```javascript
const index = comments.findIndex(comment  =>  comment.id === 823423);
comments.splice(index, 1);
console.log(comments); // (4) [{…}, {…}, {…}, {…}]
```

---

3. Array.prototype.slice()
- 기존 배열을 보존하고 싶을 때 사용할 수 있는 방법
```javascript
const index = comments.findIndex(comment  =>  comment.id === 823423);
const newComments = [
  ...comments.slice(0, index),
  ...comments.slice(index + 1)
];
console.log(newComments); // (4) [{…}, {…}, {…}, {…}]
```
