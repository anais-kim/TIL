Elastic Beanstalk with Port
========
Elastic Beanstalk use proxy to send request on 80 port to other port, such as 8081.  
Defalt ports are different among containers.
- node.js: 8081
- java: 5000

So if you don't want to use default port on your local environment, you have to use like this in node.js
```node
var port = process.env.PORT || 3000;
var server = app.listen(port, function () {
  console.log('Server running at http://127.0.0.1:' + port + '/');
});
```
and in java.
```java
System.getProperty("PORT")
```
