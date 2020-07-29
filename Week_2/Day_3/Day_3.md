# What's in a URL
* Protocal
* Domain
* Path
* Query String
* Fragment

## Client
Front end , where your client (i.e. user) get to see
They can connect to your server via browser (e.g. Chrome, Firebox)
Send request to server (in form of URL) for the resources

## Server
Back end, where you store the resource and receive request from client, and export the resource

# HTTP Hyper Text Transfer Protocal
It is a protocal, a set of rules to follow when doing things.
In this situation it's rules to follow when computer doing data transfer.

## FTP, NTP, HTTPS, HTTP, TCP, UDP, POP3, SMTP, DNS, DHCP, IMAP, BitTorrent

# TCP 
Built on top of IP - dividing a file into segments to be sent through IP and combining those segments back into a file when they are received.
## connection oriented
Both parties have to agree to connect before being connected (phone call) (text message is considered connection less, D pic! You did not agree to it but still received them)
## Congestion control 
Pick the least congested path, may not be the shortest, but would be faster because less traffic 
Even the load so the highway doesn't get overflow
## Error Detection, Lost Data Handling
## Adds Ports
Ports helps as IP doesn't know what application should be receiving the package. They have your address(IP) but they don't know which floor, which suit# 

# UDP
## It doesn't get stop because of small package lost
e.g. Zoom/ Twitch  Some thing that is live streaming 

> Fast but small bandwidth v.s. Small but large bandwidth
> Speed (ping/ms) vs Volume (bandwidth/mps)
> Small smart cars going back and fore very fast and keep sending little packages
> Semi track which goes slow, but carries a large package (composed of lots of small packages), and have everything delivered in 1 go

# Net module
## const net = require('net') // It comes with Node
``` javascript
const net = require('net'); // get the new module that does server/client thing
const server = net.createServer(); // this program is considered server as you are making it a server

// Input/Output (I/O)- will be done async by java

const connections = []// to keep a record of who connected

server.on('connection', (conn)=> { // listener : when server.on connection happens, do the callback
  conn.setEncoding('utf8')// to make sure what server send is something client can read
  connections.push(conn);
  conn.on('data', (data)=>{ // check for 'data' if happens, do the callback function
    console.log(data);
    for (let connection of connections) {
      connection.write(data);
    }
  })
  conn.write("You have connected to the super secret chat server."); // send something to the client(conn) on connection
  console.log("do sth when connection occurs");
});

const port = 3000;

console.log("listening on port " + port);
server.listen(port) // tell your server where/what should it listen to , like radio channel dev use 3000+
```


# Curl
You can contact a server and get data back within command line
```curl -v http://sample.com ```
The request is 
GET /         - the method (GET: retrieve data/POST: add data/PUT: edit data/DELETE: remove data)
HOST:         - who / which server you are trying to contact
User-Agent:   - what program is used to making this request (Chrome/ Curl)
Accept: */*

## GET 
Safe operation, would not change the server
## POST
Unsafe, will mutate the server states. You add something
They have optional body (the information to add)
## PUT
Unsafe, will change the server states. You replace something
They have optional body (the information use to replace)
## DELETE
Unsafe, will change the server states. You remove something

# Check out Http:cat
You can see what status code stands for, with an image of a cat to represent it 🐱


## Tools to test
### Postman
- Specify which method you are using (GET/ POST/ PUT) etc
- Paste the URL next to the method
- Make changes to key and details if you want
- Press send
- See what is the response from the server 