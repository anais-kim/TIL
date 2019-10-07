### Sort Without Articles

- Articles: *A*, *An*, *The*
- Use regular expression like below:

```javascript
const bands = [
  'The Plot in You',
  'The Devil Wears Prada',
  'Pierce the Veil',
  'Counterparts',
  'A Skylit Drive',
  'Anywhere But Here',
  'An Old Dog'];

function strip(text) {
  return text.replace(/^(a |an |the )/i, '').trim();
}

const sortedBands = [...bands].sort((a, b) => strip(a) > strip(b)? 1 : -1);
console.log(sortedBands); 
/* [
	"Anywhere But Here", 
	"Counterparts", 
	"The Devil Wears Prada", 
	"An Old Dog", "Pierce the Veil", 
	"The Plot in You", 
	"A Skylit Drive"
  ] */
```
