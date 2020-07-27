# Package and npm
What is a package - a self contained library that we can install and use 

(What's a library? go back and read [this](https://web.compass.lighthouselabs.ca/ed35cdc0-fb9e-434c-a7d5-58c48372b969))

# What is [package.json](https://docs.npmjs.com/files/package.json)

It looks kind of like this
```shell
{
  "name": "project-name",   //basic attributes
  "version": "1.0.0",       //basic attributes
  "description": "Short project summary", 
  "main": "index.js",
```
## Scripts
### Custom scripts go here
Let you run command as using an alias
Example "npm run myscript"
>```shell
>  "scripts": {  
>    "myscript": "ENV=development node index.js",
>    "test": "echo \"Error: no test specified\" && exit 1"
>  },
>  "author": "",
>  "license": "MIT",
>  ```
## Dependencies
### A list of of packages that need to be installed for this project to run properly
Example here is a package named express, and need ver. ^4.13.4
>  ```shell
>  "dependencies": {
>    "express": "^4.13.4"
>  }
>}
>```