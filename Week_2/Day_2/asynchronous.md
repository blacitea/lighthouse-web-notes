# Asynchronous Control Flow

## What is wrong with synchronous control flow? 
> ### Blocking Code
> Play around in the rapple 
> new Date()
> new Date().getTime() - return an int , time in ms from Jan 1 1970 sth sth
> ```
> for (let i = 0; i < 1000; i++) {  // This for-loop is BLOCKING 
  const date = new Date().getTime();
> console.log(date);
> }
> const name = 'Andy';
> console.log(name);                // this guy
> ```



## SetTimeOut (If you want something(the callback!) to run once at some point)
> ### setTimeout(handler, timeout?)
> handler = sometime to do when things happen = the callback function
> timeout = how long we want to wait, before we run the callback
>> setTImeout(()=>{console.log('inside the callback)}, 3000) // each setTimeout run syn, the callback inside is asyn
>> setTImeout(()=>{console.log('inside the second callback)}, 2000) //
> javascript register 1st setTimeout, take the callback in and the timer in, then javascript register the 2nd setTimeout, take the 2nd callback in and the secord timer in
>> when the timer ran out, the callback function happens 
>
> ### asynchronous is possible because of Node.js
> Node is the run time environment
> Node has an event loop keep running in the background
>> It check if any handler is ready to run / if an event happens, that would trigger a handler
>
> ### Most event listener is listening for external event, setTimeout is an internal event
>
> ### All syn code run through first, then asyn code will run 
>> you can set some code to run after all syn code run, by making setTimeout(()=>{},0) << This run immediately the whole code finish running
>> Read asyn code as your computer would run it, not as how it was written
> ### Declare a function doesn't mean you executed the function
> Things only happens when you call a function
> ### A higher function doesn't give you a explicit return, usually it is an implicit return (undefined)
> When utalizing higher functions, make use of the callback function to return a value
> 
## Set-Interval (If you want something(the callback!) to run more than once)
> ### setInterval(handler(callback), time)
> setInterval(()=>{}, time)
> setInterval(callback, to run callback after this time interval again)
> ### clearInterval(object where you store your setInterval)
> const interval = setInterval(()=>{}, time);
> clearInterval(interval);
> to clear your set-interval when a condition is met
> set a var to keep track the iteration/ base condition
> set a logic to check the iteration/ current state of condition
> if logic checks out, run clearInterval, to stop the callback inside set-interval running


## File System Functions [(`fs`)](nodejs.org/api/fs.html)
> ### Built in node function, let you load file
> const fs = require('fs');
> We learn fs.readFile & fs.readFileSync today
> The one without "Sync" takes a callback, so we know it do it async
> loremANum will print you some lorem ipsm automatically inside html
>> ### fs.readFileSyng(path, option{encoding etc})
>> const myFile = fs.readyFileSync('./index.txt',{encoding: UTF8});
>> console.log(myFile.length);
>
>> ### fs.readFile(path, options{encoding etc}, callback(err, data)=>{})
>> ```javascript
>> fs.readFile('./index.txt', {options}, (err, data)=>{
>>  if (err) throw err;
>>
>>  console.log(data.length);
>>});
>>
>>console.log(is this async?)
>> ```
>> When you read a file, it is just a javs string, that you can run with your callback
>> There is not return value from your asyn function