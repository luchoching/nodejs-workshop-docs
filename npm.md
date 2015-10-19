# NPM 

https://docs.npmjs.com/

npm is the package manager used to distribute Node modules.

`npm --help`

`npm init`

`npm init -y` : 什麼都yes, 方便快速prototyping 

`package.json`

http://www.copterlabs.com/blog/json-what-it-is-how-it-works-how-to-use-it/

JSON is short for JavaScript Object Notation, and is a way to store information in an organized, easy-to-access manner. In a nutshell, it gives us a human-readable collection of data that we can access in a really logical manner.

`npm search packagename`

`npm install` 又可簡寫為 `npm i`

`npm install --save`, `npm install --save-dev`

查看全域安裝了哪些package: `npm list -g --depth=0`

查看該專案安裝了哪些packages: `npm list --depth=0`

使用別人專案的第一個動作, 就是查看package.json , 然後`npm install`

[Top 100 most dependent upon packages](https://github.com/anvaka/npmrank/blob/master/sample/dependencies.md) 

[npm數量全世界最多](http://www.modulecounts.com/)

### library update

注意專案要更新library是大事, 要小心

### npm scripts

特殊: `npm start`, `npm test`

`npm run`
