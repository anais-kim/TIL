Mocha Getting Started
======================

1. install
```bash
npm install mocha
```

2. make test script
```javascript
var assert = require('assert');
describe('Array', function() {
  describe('#indexOf()', function() {
    it('should return -1 when the value is not present', function() {
      assert.equal(-1, [1,2,3].indexOf(4));
    });
  });
});
```

3. run test
```bash
./node_modules/mocha/bin/mocha
```

4. make test script in package.json & run test
```json
 "scripts": {
    "test": "mocha"
  }
```
```bash
npm test
```
