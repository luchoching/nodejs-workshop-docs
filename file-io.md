# Path, File

## Path 

https://nodejs.org/api/path.html  

`require('path')`

> path.join([path1][, path2][, ...])

Join all arguments together and normalize the resulting path.

> path.resolve([from ...], to)

Resolves to to an absolute path.

就像 `cd` command

## File 

https://nodejs.org/api/fs.html

`require('fs')`

The asynchronous form always takes a completion callback as its last argument. 

The arguments passed to the completion callback depend on the method, but the first argument is always reserved for an exception. <-- 典型的Node.js慣例!

If the operation was completed successfully, then the first argument will be null or undefined.

**Async & Sync method** : When using the synchronous form any exceptions are immediately thrown. You can use try/catch to handle exceptions or allow them to bubble up.

### 刪除檔案(Async version)

### 刪除檔案(Sync version)

### 順序性? :)

### 常見操作

查詢目錄,  檢查檔案是否存在, 讀取/寫入檔案, 新增/刪除檔案: 

http://www.devdungeon.com/content/file-manipulation-nodejs

ReadStream, WriteStream

## Async flow 

結果為?? 

``` js
var fs = require('fs');

console.log('start reading dir...');

fs.readdir('./', function(err, files){
  if (err) console.error(err);
  console.log(files);
});

console.log('end reading dir');
```

要怎麼控制執行的順序呢? 

## Node.js Error Handling

慣例 `err`是callback的第一個參數: 

``` js
var fs = require('fs');

fs.unlink('./test.txt', function(err){
  if (err) throw err;
  console.log('Del sucessful!');
});
```

throw error or console.error it: 

``` 
$ node del-file
/Users/luchoching/code/nodejs-test/del-file.js:4
  if (err) throw err;
           ^

Error: ENOENT: no such file or directory, unlink './test.txt'
    at Error (native)
```

`ENOENT`: Error NO ENTry

練習: 先check檔案是否存在 --> 刪除檔案

## Links 

[Joyent: Error Handling in Node.js](https://www.joyent.com/developers/node/design/errors)



https://masteringmean.com/lessons/399-Using-Nodejs-to-Access-the-File-System

http://www.sitepoint.com/accessing-the-file-system-in-node-js/
