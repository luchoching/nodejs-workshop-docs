# Module

https://nodejs.org/api/modules.html

Node.js has a simple module loading system.

In Node.js, **files and modules are in one-to-one correspondence**

A module encapsulates related code into a single unit of code. When creating a module, this can be interpreted as moving all related functions into a file.

撰寫一個module : `say.js`

```
var hello = function(){
  return 'Hello';
}

var helloSpanish = function(){
  return 'Hola';
}

module.exports.hello = hello;
```

ps. function is a object, too.

Modules make it possible to include other Javascript files into your applications.

引用一個module: `main.js`

```
var say = require('./say');

console.log(say.hello());
//console.log(say.helloSpanish());
```

有export的,就像是public, 沒有export的, 就是private

`module.exports` or `exports` ? 參考[官網說明](https://nodejs.org/api/modules.html#modules_the_module_object):

>In each module, the `module` free variable is a reference to the object representing the current module. For convenience, `module.exports` is also accessible via the exports module-global. module isn't actually a global but rather local to each module.

`module.exports`: 

> The `module.exports` object is created by the Module system. Sometimes this is not acceptable; many want their module to be an instance of some class. To do this, assign the desired export object to module.exports. Note that assigning the desired object to exports will simply rebind the local exports variable, which is probably not what you want to do.

`exports`: 

> The exports variable that is available within a module starts as a reference to module.exports. As with any variable, if you assign a new value to it, it is no longer bound to the previous value.

### Share variables between modules

config.js: 

```
var config = {
  foo: 'bar'
};

module.exports = config;
```

server.js:

```
var config = require('./config');
console.log(config.foo);
```

### require all files in a folder 

http://stackoverflow.com/questions/5364928/node-js-require-all-files-in-a-folder

## Core modules 

https://nodejs.org/api/

Core modules are always preferentially loaded if their identifier is passed to `require()`. 

For instance, `require('http')` will always return the built in HTTP module, even if there is a file by that name.

## Links

https://www.airpair.com/javascript/node-js-tutorial#1-introduction

node_modules