# Module
## Every file in Node is a Module

You can check the value of the module (of your js file) by this code
>``` shell
>console.log(module);
>```

When you run the file with above code inside, something like this will print
>``` shell
>Module {
>id: '.',
>  exports: {},
>  parent: null,
>  filename: '/Users/superman/codes/moduleCheck.js',
>  loaded: false,
>  children: [],
>  paths: [ ... ] 
>}
>```

## Make your code exportable (require-able)
### AKA - can be accessed by another file

Let's say you have a function - helloWorld.js
>```javascript
>const sayHello = function(name) {
>  console.log("Hello, ", name);
>}
>```

In order for another file to read this function, you have to EXPORT it / so that it can be required
>``` javascript
>module.exports = sayHello; // export the variable that store the function
>```

Now if you want to use the function in another file, called helloMichael.js.
>``` javascript
>const sayHello = require('./helloWorld'); //Import via require(relative path) in this case, assume in same directory - Name of the file you require from
>console.log('sayHello is:', sayHello);
>sayHello('Michael');
>```