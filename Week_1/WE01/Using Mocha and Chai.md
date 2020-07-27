# Unit Testing with Mocha and Chai [READ](https://www.sitepoint.com/unit-test-javascript-mocha-chai/)

>**Make sure you already ```npm init``` and have your package.json ready before doing the below.** ```npm init -y``` if you want to say yes to all questions.

## Install Mocha (npm required, check [npm install](http://www.sitepoint.com/beginners-guide-node-package-manager/))

>For browser testing ```npm install mocha chai --save-dev```

> For Node.js code testing ```npm install -g mocha```

## IMPORTANT
> To test in console/ Node.js, you need to include 
>> ```javascript
>> var chai = require('chai');
>> ```
> at the top of your test file

## Directory Structure
>It is better to keep your test in another directory from your main files.
> 
>That means, one file for code, one file for test
>> * ProjectDir
>>    * code/
>>        * main.js 
>>    * test/
>>        * test1.js *(This is a test case)*
>>        * test2.js *(This is another test case)*

## Writing a Test Case
Every test file have same basic pattern
> ### ```Describe``` Block
>> ```javascript
>>describe('Array', function() {
>>  // Further code for tests goes here
>>});
>> ```
>Describe is used to group individual test. 
> * Frist parameter - what we are going to test , in this case,  ```Array```.
>> ```javascript
>> describe('Array', function() {
>>  it('should start empty', function() {
>>   // Test implementation goes here
>>  });
>>
>>  // We can have more its here
>> });
>> ```
> * ```it``` block - create actual test, can have multiples ```it```s. 
>    * The first parameter of ```it``` should be a people readable string to describe the test

In case of node version error, and it say mocha cannot be found
update package.json with 
```
"scripts": {
  "test": "./node_modules/mocha/bin/mocha"
}```