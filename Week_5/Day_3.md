# SQL from our Apps
* get javascript to talk to server
```javascript
const pg = require('pg');
const Client = pg.Client;

const options = {
  user:'',
  password: '',
  database:'',
  host:'localhost',
  port:'5432' // default, can skip
}

const client = new Client();

client.connect(()=>{  // connect the client, take a callback once connected

})

client.query('query string') // this return a promise when no callback given
  .then((response)=>{
    response.rows
  })

client.end();
```