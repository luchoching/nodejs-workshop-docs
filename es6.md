# ES6

REPL strict mode: `env NODE_REPL_MODE=strict node`

## 利用babel轉換node還沒實作的部分

check node.js ES6還沒實作的部分:`node --v8-options | grep "in progress"`

ex: for + Map destucture, modules


http://www.2ality.com/2015/04/node-es6-transpiled.html

blacklist regenerator

.babelrc

## var, let, const

### var 

var: 將變數往上浮昇一個等級

``` js
function getValue(condition){
  if (condition){
    var value = 'blue';
    console.log(value); //blue
  } else {
    console.log(value);
    return null;//false --> undefined
  }
  console.log(value); //blue
}

  getValue(true);
```

else block仍然可以存取 value變數(值為undefined, 因為其值還沒有初始化 )

所以建議利用`let`來使用block scope, 上述將var改let, 那else block就找不到value了

### let, const 

let --> 不能重複宣告 

``` js
var count = 30;
let count = 30; //err
```

var, let: 

``` js
'use strict';

var value = 'blue';

function getValue(condition){
  if (condition){
    let value = 'blue';
    console.log(value);
  } else {
    console.log(value);
    return null;
  }
  console.log(value);
}

getValue(false);
```

const --> must be initialized and cant be reinitialized. block-level.

### Declaring Objects with Const

``` js
const person = {
    name: "Nicholas";
};

// works
person.name = "Greg";

// throws an error
person = {
    name: "Greg"
};
```

**const prevents modification of the binding**, not modification of the bound value.

小心使用(怕browser實作跟node實作結果不同)

### The Temporal Dead Zone (TDZ)

``` js
if (condition) {
  console.log(typeof value);  // ReferenceError!
  let value = "blue";
}
```

### Block Binding in Loops 

用 var: 

``` js
for (var i=0; i < 10; i++) {
    process(items[i]);
}

// i is still accessible here
console.log(i);                     // 10
```

建議都改用let: 

``` js
for (var i=0; i < 10; i++) {
    process(items[i]);
}

// i is still accessible here
console.log(i);                     // i is not defined
```

## Functions in Loops 

早期ES5:

``` js
'use strict';

var funcs = [];

for(var i=0; i<10;i++){
  funcs.push(()=>console.log(i));
}

funcs.forEach((func)=>func()); //通通印10
```

That’s because **the variable i is shared across each iteration of the loop, meaning the functions created inside the loop all hold a reference to the same variable**. The variable i has a value of 10 once the loop completes, and so when console.log(i) is called, that’s the value it outputs each time.

ES5的解決方法, 使用 immediately-invoked function expressions (IIFEs) : 

``` js
'use strict';

var funcs = [];

for(let i=0; i<10;i++){
  funcs.push((function(value){
    return function(){
      console.log(value);
    };
  })(i));
}

funcs.forEach((func)=>func());
```

ES6解決方法, 改成let就可: 

const通常不能在for loop宣告

## String 

## Template String

## Functions 

### function with default parameters 

ES5 要寫default parameter:

``` js
function makeRequest(url, timeout, callback) {

    timeout = timeout || 2000;
    callback = callback || function() {};

    // the rest of the function

}
```

或是用typeof : 

``` js
function makeRequest(url, timeout, callback) {

    timeout = (typeof timeout !== "undefined") ? timeout : 2000;
    callback = (typeof callback !== "undefined") ? callback : function() {};

    // the rest of the function

}
```

ES6就直接有default parameters ,  **node.js 4.1.2的 chrome V8還沒有支援**

### Arrow functions 

``` js
var doNothing = () => {};
```

或是:

``` js
var sum = (num1)=> ({name: num1, test: 'hehhah'});
```

### Immediately-Invoked Function Expressions

``` js
'use strict';

let person = ((name)=>{
  return {
    getName: ()=>name
  };
})('Nicolas');

console.log(person.getName());
```


## Links

[Understanding ECMAScript 6](https://leanpub.com/understandinges6/read#leanpub-auto-octal-and-binary-literals)
