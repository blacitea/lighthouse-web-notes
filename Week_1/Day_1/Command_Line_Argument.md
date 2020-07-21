# CML Argument
## This is about how to accept arguments from user through command line using [process.argv](https://stackabuse.com/command-line-arguments-in-node-js/)
When we call a function in command line, it consist of

```shell
[0]runtime [1]script_name [2....n]arguments
```

example 
```shell
node test.js apple red 12 3
```

if we have a function inside file processargv.js
```javascript
'use strict';

for (let j = 0; j < process.argv.length; j++) {
    console.log(j + ' -> ' + (process.argv[j]));
}
```

we can call it with
```
node processargv.js 1 2 3