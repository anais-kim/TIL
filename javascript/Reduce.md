### Array.prototype.reduce()

reduce() 메서드는 배열의 각 요소에 대해 주어진 리듀서(reducer) 함수를 실행하고, 하나의 결과값을 반환합니다.

---

#### [예제] 수명의 총합을 구하기 위해 reduce()를 이용
- 초기값을 0으로 세팅 (초기값이 없을 경우 배열의 첫번째 값을 사용하게 됨)
```javascript
const inventors = [
  { first: 'Albert', last: 'Einstein', year: 1879, passed: 1955 },
  { first: 'Isaac', last: 'Newton', year: 1643, passed: 1727 },
  { first: 'Galileo', last: 'Galilei', year: 1564, passed: 1642 },
  { first: 'Sarah E.', last: 'Goode', year: 1855, passed: 1905 },
  { first: 'Lise', last: 'Meitner', year: 1878, passed: 1968 },
  { first: 'Hanna', last: 'Hammarström', year: 1829, passed: 1909 }
];
    
// How many years did all the inventors live?
const totalYears = inventors.reduce((total, inventor) => {
  return total + (inventor.passed - inventor.year);
}, 0);
console.table(totalYears);    
```

---

#### [예제] 각 교통수단의 개수 구하기
```javascript
const data = ['car', 'car', 'truck', 'truck', 'bike', 'walk', 'car', 'van', 'bike', 'walk', 'car', 'van', 'car', 'truck' ];
    
const sum = data.reduce((count, value) => {
  if (count[value]) count[value]++;
  else count[value] = 1;
  return count;
}, {});
console.log(sum); // {car: 5, truck: 3, bike: 2, walk: 2, van: 2}
```
