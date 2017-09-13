Selenium with Node.js Getting Started
======================================

1. install selenium-webdriver
```bash
npm install selenium-webdriver
```
```bash
### if you did't install webdrivers...
brew install chromedriver
brew install geckodriver
```

2. make sample.js
```javascript
const {Builder, By, Key, until} = require('selenium-webdriver');

let driver = new Builder()
    .forBrowser('firefox')
    .build();

driver.get('http://www.google.com/ncr');
driver.findElement(By.name('q')).sendKeys('webdriver', Key.RETURN);
driver.wait(until.titleIs('webdriver - Google Search'), 1000);
driver.quit();
```

3. run sample.js
```bash
node sample.js
```
