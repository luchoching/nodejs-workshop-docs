# Event-driven

來玩Node.js標準API, 並理解其開發方式特色 

## HTTP server 

https://nodejs.org/en/about/

使用Node.js API,  `hello-http-server.js`:

```
var http = require('http');

http.createServer(function(req, res){
  res.writeHead(200, {'Content-Type': 'text/plain'});
  res.end('Hello World\n');
}).listen(8000, function(){
  console.log('Server running at http://localhost:8000');
});
```

Node.js is an **asynchronous event driven** framework. 

In the above example, many connections can be handled concurrently.


## Event 

Many objects in Node.js emit events: a `net.Server` emits an event each time a peer connects to it, a `fs.readStream` emits an event when the file is opened. 

All objects which emit events are instances of events.EventEmitter. 

Functions can then be attached to objects, to be executed when an event is emitted. 

These functions are called listeners. Inside a listener function, this refers to the EventEmitter that the `listener` was attached to.

## Node.js HTTP API 

https://nodejs.org/api/http.html

`var http = require('http');`

> http.createServer([requestListener])

Returns a new instance of `http.Server`.

`http.Server` class is an `EventEmitter` with the many events.

The requestListener is a function which is automatically added to the 'request' event.

function也是Object, function可以當作參數傳到函數去

有某個event發生的時候, 就會觸發該callback function

![callback function](https://upload.wikimedia.org/wikipedia/commons/thumb/d/d4/Callback-notitle.svg/740px-Callback-notitle.svg.png)

> Event: 'request'

當我們的callback funcion (listener) 被觸發的時候, 有兩個參數被傳入

`function (request, response) { }` emitted each time there is a request. Note that there may be multiple requests per connection (in the case of keep-alive connections). request is an instance of `http.IncomingMessage` and response is an instance of `http.ServerResponse`.

> server.listen(port[, hostname][, backlog][, callback])

The last parameter callback will be added as a listener for the 'listening' event.

## 結論

如上例, Node.js可以同時處理很多連線(**concurrency**), 只要有連線進來, 就會發送request event, 觸發對應的listener callback fuction(requestListener)

Users of Node are free from worries of dead-locking the process—there are no locks(**non-blocking**).




