Promises
============

https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Promise

## 1. Create Promises
```javascript
/**
   * XHR wrapped in a promise.
   * @param  {String} url - The URL to fetch.
   * @return {Promise}    - A Promise that resolves when the XHR succeeds and fails otherwise.
   */
  function get(url) {
    return new Promise(function (resolve, reject) {
      var req = new XMLHttpRequest();
      req.open('GET', url);
      req.onload = function() {
        if (req.status === 200) {
          resolve(req.response);
        } else {
          reject(Error(req.statusText));
        }
      };
      req.onerror = function() {
        reject(Error('Network error'));
      };
      req.send();
    });
  }

 get('../data/earth-like-results.json')
 .then(function resolve(response) { addSearchHeader(response);},
       function reject() { addSearchHeader('unknown');})
 .catch(function error() { addSearchHeader('unknown');});
 ```

## 2. Chaining Promises
```javascript
getJSON('../data/earth-like-results.json')
.then(function (json) {
  addSearchHeader(json.query);
  return getJSON(json.results[0]);
}).catch(function () {
  addSearchHeader('unknown');
}).then(function (data) {
  createPlanetThumb(data);
}).catch(function () {
  addSearchHeader('unknown');
});
```

## 3. Promises Array
### 3-1. Using sequence
Request in order, but not parallel (in series)
```javascript
getJSON('../data/earth-like-results.json').then(function (response) {
  var sequence = Promise.resolve();

  response.results.forEach(function (url) {
    sequence.then(function () {
      return getJSON(url);
    }).then(createPlanetThumb);
  });
});
```

### 3-2. Using map
Request parallel, but not in order
```javascript
getJSON('../data/earth-like-results.json').then(function (response) {
  response.results.map(function (url) {
    getJSON(url).then(createPlanetThumb);
  });
});
```

### 3-3. Using Promise.all();
Request parallel, and in order!!
```javascript
getJSON('../data/earth-like-results.json')
.then(function(response) {
  addSearchHeader(response.query);
  return Promise.all(response.results.map(getJSON));
})
.then(jsonList => {
  jsonList.forEach(createPlanetThumb);
});
```
