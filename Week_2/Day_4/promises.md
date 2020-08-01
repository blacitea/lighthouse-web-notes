# Promises
We are learning how to use existing promises from other program/function that we use.
If we learn how to create promises, would be a little bit only.

## Revision
### Why we use callback
* Keep our function has 1 specific purpose / Modular / Easy read, write, test
* Allow us to work async flow
### What is Asyn flow
* Non blocking work flow even with Input/Output task
    * task 1 sync
    * task 2 async has heavywork(I/O), with a callback -> register on Event Queue
    * task 3 sync
    * task 4 async has heavywork(I/O), with a callback -> register on Event Queue
    * task 5 sync
    * task 6 sync

Javascript will run through ALL async code first, ONLY AFTER all sync code are done, THEN Javascript will check the event queue. 
It will then keep running the event loop until an async is completed(event happens), and let Javascript know, and it will do whatever that async callback is supposed to do.

## Why need promises
To avoid callback Hell, where you nest callback inside callback inside callback
Example - The profile making Survey.js !
1. You don't want question 2 asked until question 1 answered, so you nested Q2 inside Q1 and so on.
2. We have a single error handling with catch (.catch((err)=>{do sth when err is true}))
3. Have to use callback because of the function we are using
4. More maintainale
5. Easier to provide extra behaviors/ method for future usage

## Maybe callback instead?
1. We have to declare less function
2. Simpler to understand (for now/ only 1 asyn)
3. Maybe memory use? (maybe you can do it better somewhere else too!)

## Re-do with promises
``` javascript
const readline = require('readline-promise').default;
const rlp = readline.createInterface({ // an object to give how you do I/O

})
rlp.questionAsync('what is your name') // This will return a promise 
  .then(/*callback here*/ (res) =>{   // .then = Promise.then, it will run when async was successful 
    /*things to do by callback*/
    console.log("the user said:", res);
  })
  .catch((err) => { // will run if async thing failed .catch is a method

  })
``` 