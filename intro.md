# Introduction 

## Node.js 

browser --> server side

Node.js = 一個執行環境 + 函式庫

Node.js: an **asynchronous**, **event-driven** framework built on top of **Chrome's JavaScript V8 engine**

pic from [server check.in](https://servercheck.in/blog/moving-functionality-nodejs-increased-server): 
![img](https://servercheck.in/sites/servercheck.in/files/node-drupal-queue-comparison.jpg)


Node is **single-threaded** and uses a concurrency model based on an event loop.

 It is **non-blocking**, so it doesn't make the program wait, but instead it registers a **callback** and lets the program continue. 

This means it can handle concurrent operations without multiple threads of execution, so it can scale pretty well.


Nodejs is not designed for data processing. It's good for tasks such as getting data from database, doing simple transform and send user response.  

## JavaScript, ECMAScript 

[wiki](https://en.wikipedia.org/wiki/ECMAScript):

>ECMAScript is a trademarked[1] scripting language specification standardized by Ecma International in ECMA-262 and ISO/IEC 16262. Well-known implementations of the language, such as JavaScript, JScript and ActionScript are widely used for client-side scripting on the Web.

[stackoverflow](http://stackoverflow.com/questions/912479/what-is-the-difference-between-javascript-and-ecmascript): 

>JavaScript = ECMAScript + DOM API

ECMAScript® Language Specification defines all logic for creating and editing objects, arrays, numbers, etc...

DOM API makes it possible to communicate with HTML/XML documents

History of JavaScript naming: 

Mocha ► LiveScript ► JavaScript ► (part of JS resulted in) ECMA-262 ► ECMAScript ► JavaScript (consists of ECMAScript + DOM API)

## ECMAScript 5, 6, 7

[ECMAScript 2015 spec](http://www.ecma-international.org/ecma-262/6.0/index.html)

[ES6 in Node.js](https://nodejs.org/en/docs/es6/)

```
node --v8-options | grep "in progress"
node -p process.versions.v8
```

[Babel](https://babeljs.io/) is a JavaScript compiler.

## Links 

http://www.slideshare.net/jguerrero99/seattle-strongloop-nodejs-workshop
