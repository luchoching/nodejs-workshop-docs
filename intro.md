# Introduction 

Node.js: an **asynchronous**, **event-driven** framework built on top of **Chrome's JavaScript engine**

Node is **single-threaded** and uses a concurrency model based on an event loop.

 It is **non-blocking**, so it doesn't make the program wait, but instead it registers a **callback** and lets the program continue. 

This means it can handle concurrent operations without multiple threads of execution, so it can scale pretty well.


Nodejs is not designed for data processing. It's good for tasks such as getting data from database, doing simple transform and send user response.  

So I would like to have nodejs as a Restful API server and talk to Scala, which runs complex and long tasks.
