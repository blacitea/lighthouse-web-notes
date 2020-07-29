# OMG What are event listeners

## Connection related

### Client side
You need to be connected for the below listener to work.

Because they need a connection to listen to!

> #### Getting connected
>
> ``` javascript
> const net = require('net');
> const connect = function () {
>   const conn = net.createConnection({
>     host: 'Server IP Address',
>     port: 'host port',
>   });
>   return conn;
> };
> ```
>
> Okay, you are connecting now with some server

Once you have the connection going, 

You can have a list of event listener, listening to the connection, to listen for some events

> #### conn.on('data', (data)=>{do sth with or without using data})
> #### conn.on('connect', ()=>{do sth when connection happends})
> #### 