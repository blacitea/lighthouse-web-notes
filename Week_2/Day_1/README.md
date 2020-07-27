# TTD - Unit Testing

## Manuel Testing
>It is hard to to verify console log result.
>Using ```return``` instead, you can test it
 more readily and easily. 

>(List of test name) Alice Bob Carol Dean Ellen

Manuel testing is labour taxting, cause man power! 

``` javascript
console.assert((something to test, return true/false), (message to print if parameter returns false));

console.assert(1 !== 1, 'not equal');
// will print Assertion fail: not equal

console.assert(1 === 1, 'not equal');
// nothing happens, because it evaluate true
```

### Nodejs.org 
> Assertion Library
When you google about assert, make sure to include node 

Because we call method of assert with . (e.g. assert.equal), we know that assert is an object.

>> if you see [message] in documentation, what means the [message] is optional, not compulsory to use the method.
>> if you see ```message?``` when coding, the ```?``` means that part is optional.


```const assert = require("assert").strict```

> All require statement should be in top of file
> * Declare before use to avoid error, make them ready for use
> * A flag to other devs to know what is required

You can change what you name the var to do require, for convenient usually use the same keyword

As soon as Node hits an error, it will completely shut down. The line with error is the last line it will run.

``` assert.equal ( 1, "1") ``` Non strict equal (==) used, which means no error
``` assert.StrictEqual ( 1, "1") ``` Strict equal (===) used, which mean error will show

> ```require("assert").strict``` the ```.strict``` is to enforce strict mode
> Always make sure you use ```.strict```, you don't want on coerion on your assertion!!!

## Keep your test code(assert.equal etc.) away from your production code(code that is user facing)!!! 

Node considered every js file as a module
[Module Node.js]()

Driver code = code that runs your function, so it can be tested out 

## Module.exports
To get it out so you can require it somewhere else! 

> ```module.exports = sayHello;``` single thing
> ``` 
> module.exports = {
>    sayHello: sayHello
>};
> ```
> multiple things to export
> ```
>module.exports.sayHello = sayHello;
>```
>Good for export single thing (i.g. Object.key = value)


> If it is something we did not right, we use the name of the module("Chai", "Assert" etc.) to call it in require

>If it is something that we write, we use a relative path ("./say-Hello")to call it

If expect is an object with multiple keys/method

Your require have to be specific, or have another declaration to grab the exact mehtod you want

``` javascript
const myObj = require("./sayHello.js")

const sayHello = myObj.sayHello;
```

# Mocha - a testing framework
It runs every single test that it knows about
Mocha is outside of Node
## [NPM](npmjs.com)
It is A node package manager, not the only one
e.g. yam 

### Dependency 
What our project depends on to run property
If you missing one of your dependency, it won't work

> ## Step 1 - npm init
> ``` npm init ``` it helps you create your package.json file
> entry point : for web server, the single entry point to your server if you have one
> git repository : the link to your git repo on github (SSH/Html would work)
> ### You need your package.json to store your dependencies! 
> ### npm [Mocha] (npmjs.com/package/mocha)
>
> [How to use it?](mochajs.org) INSTALLATION
>
> ``` npm install --global mocha ``` 
> 
>Dependencies we use for running the production code --global flag
> Make it a dependency for your project, people who share your project will install it when they fork/clone, so your project will run correctly
> ``` npm install --save-dev mocha ``` dependencies we use only when we were writing code --save-dev flag

> We can use this to trigger mocha run, put it in your package.json - scripts - test to make it easier!
> ``` "test" : "./node_modules/mocha/bin/mocha" ``` so we can run it with just ``` npm run test ```
> ```
>./node_modules/mocha/bin/mocha
>```
> For mocha, if no error was throw during the code runs (inside it), your test passed
> Mocha doesn't actually check if what you expect happened
> ``` throw new Error('Oooops')```
>
> That's why we need assert!
> So an error was throw if actual !== expected, and mocha can register it

## [Chai](chaijs.com/api/assert) - an assertion library
We can pair it up with Mocha for test.

Chai is the library that bring us assert functions.
Chai is nice because it has hundreds of assertion (isDefined(), isFunction() etc.)

``` npm install chai --save-dev```

# DO NOT add your node_modules to your gitHub
## We want our git to ignore the node_modules
If you see node_modules when you check git status:


