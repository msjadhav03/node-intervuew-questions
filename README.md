# NodeJS

### <span style="color: red;">1. What is Node.js?</span>

- open-source
- cross-platform
- runtime Environment
- runs Javascript outside the browser
- created by Ryan Dahl

### 2. How to avoid callback hell?

- independent functions - modularization
- use of async and await
- use of promises

### 3. When to use worker process or background process?

- highly intensive data proccessing task

### 4. What are types of API function in Node.js?

- Blocking functions - Blocks other codes from executing
- Non-Blocking - Do not block other code form executing - all i/o operations done concurrently

### 5. What is chaining in Node.js

Output of one stream is connected to another stream. Creating chain of multple stream operations.

### 6. What are streams in Node.js?

Streams helps to read and write data from destination as continous proccess.

- read stream
- write stream
- read and write stream
- duplex stream - performs processing as per available input

### 7. What is package.json?

- heart of the application
- manifest
- metadata about application
- properties of application

### 8. What is module.exports ?

Encapsulating same or interelated code in single unit

### 9. What are security implementations Node.js provide?

- Authentication
- Error handling

### 10. What is functionality of 'url' module in Node.js?

handles urls, query string and individual compenents - protocal, hostname, pathname, query

- parsing URL - url.parse()
- formatting url - url.format()
- Resolving url - url.resolve()

```js
const url = require("url");

const urlString =
  "https://www.example.com:8080/path/to/resource?query=value#fragment";

const parsedUrl = url.parse(urlString);
console.log(parsedUrl);

const formattedUrl = url.format(parsedUrl);
console.log(formattedUrl);

const resolvedUrl = url.resolve("https://www.example.com/", "newpath");
console.log(resolvedUrl);

const params = new url.URLSearchParams(parsedUrl.query);
params.append("newParam", "123");
console.log(params.toString());
```

Output

```js
Url {
  protocol: 'https:',
  slashes: true,
  auth: null,
  host: 'www.example.com:8080',
  port: '8080',
  hostname: 'www.example.com',
  hash: '#fragment',
  search: '?query=value',
  query: 'query=value',
  pathname: '/path/to/resource',
  path: '/path/to/resource?query=value',
  href: 'https://www.example.com:8080/path/to/resource?query=value#fragment'
}
https://www.example.com:8080/path/to/resource?query=value#fragment
https://www.example.com/newpath
query=value&newParam=123
```

### 11. What is Middleware in Node.js?

- function having access to request, response object and next function
- executes any type of code
- can modify request and response object
- invokes next middleware

### 12. What is libuv?

- multi-platform support liabrary in Node.js
- Used for async I/O - concurrency and responsiveness
- Event loop management - handling multiple concurrent operations
- Networking - building scalable network application - DNS lookup , create and manage n/w sockets, supports TCP and UDP
- File Management - handling non-blocking I/O opearations
- Timers and Event Scheduling - set timers and schedule events
- Thread pool - intensive task leads to event loop blockage - helps to create multple thread - avoid event loop blockage
- Child Process - To run asynchronously
- Error Handiling - handling errors, recovering from failures, and reporting errors to application code.

### 13. What are the two argument async.queue takes?

async.queue -
creates Queue object to do asynchronus processing

1. Worker function - function to do process
2. Concurrency Limit - no of tasks that executed concurrently.

```js
const async = require("async");

// Define the worker function
function processTask(task, callback) {
  // Process the task asynchronously
  console.log(`Processing task: ${task}`);
  setTimeout(() => {
    console.log(`Task ${task} completed`);
    callback(); // Call the callback to signal task completion
  }, 1000);
}

// Create a queue with a concurrency limit of 2
const taskQueue = async.queue(processTask, 2);

// Add tasks to the queue
taskQueue.push("Task 1");
taskQueue.push("Task 2");
taskQueue.push("Task 3");
taskQueue.push("Task 4");
```

processTask - Worker function
2 - concurrency Limit

### 14. Spawn vs Fork

Both used to create child process

- Spawn

  1. used to run commands, shell scripts and capturing output
  2. creates new process and executes commands

  ```js
  const { spawn } = require("child_process");
  const ls = spawn("ls", ["-l", "-a"]); // Spawn 'ls' command with arguments

  ls.stdout.on("data", (data) => {
    console.log(`stdout: ${data}`);
  });

  ls.on("close", (code) => {
    console.log(`Child process exited with code ${code}`);
  });
  ```

- fork

  1. ideal for CPU intensive task
  2. child and parent proccessing communication - using IPC - inter process communication
  3. utilizing multiple CPU cores

  ```js
  const { fork } = require("child_process");
  const child = fork("child_script.js");

  child.on("message", (message) => {
    console.log(`Received message from child: ${message}`);
  });
  child.send("Hello from parent!");
  ```

### 15. What is ExpressJS and Purpose of ExpressJS

It is minimal and flexiable web application framework
Features

1. Routing
2. RESTful APIS
3. Middleware Ecosystem
4. Template Engine
5. Serving Static Files
6. HTTP Utility Methods


[1. Asynchronous and Non-Blocking](#Asynchronous)
[2. Event Loop](#eventloop)
[3. Modules](#modules)
[4. CommonJS](#commonjs)
[5. NPM](#npm)
[6. EventEmitters](#eventEmitter)
[7. Streams](#streams)
[8. HTTP Module](#http)
[9. Express.js](#expressJS)
[11. Callback Hell](#callbackhell)
[12. Error Handling](#errorHandling)
[13. Concurrency and Scaling](#concurrenyAndScaling)
[14. fs](#fs)
[15. http](#httpModule)
[16. path](#path)
[17. os](#os)
[18. events](#events)
[19. util](#util)
[20. crypto](#crypto)
[21. stream](#stream)
[22. querystring](#querystring)
[23. url](#url)
[24. Modules and NPM](#modulesAndNPM)
[25. Middleware](#middleware)
[26. Promises and async/await](#promisesAndAsyncAwait)
[27. Clutser and Child Processes](#clusterAndChildProcess)
[28. Memory Management](#memoryManagement)
[29. Security](#security)
[30. Debugging and Profiling](#debugging)
[31. Caching and Performance Optimization](#cachingAndPerformanceOptimization)
[32. Websocket](#websocket)
[33. Authentication and Authorization](#authenticationAndAuthorization)
[34. Microservices](#microservices)
[35. Docker and Containerization](#docker)
[36. GraphQL](graphql)
[37. REST](rest)
[38. Kafka](#kafka)
[39. RabitMQ](#rabitmq)
[40. GRPC](#grpc)
[41. Serverless Architecture](#serverlessArchitecture)
[42. Testing and Test Automation](#testing)
[43. Depedency Injection](#dependencyInjection)
[44. Performance Monitoring and Profiling](#performanceMonitotring)
[45. Internationalization](#internationalization)
[46. Web Assembly](#webAssembly)
[47. Real Time Data Processing](realTimeProcessing)
[48. Hot Module Replacement](#hotModuleReplacement)
[49. Server Side Rendering](#serverSideRendering)
[50. Serverless Framework](#serverlessFramework)
[51. Service Workers](#serviceWorkers)
[52. Error Codes](#errorCodes)
[53. import vs require](#importVsRequire)


# Asynchornous and non blocking
- Asynchronous : Asynchronous programming refer to the ability to execute multiple operations concurrently without waiting for other operation to complete
- Non-blocking : Program initates an I/O operation the program does not wait for that operation to finish. 
- why need asynchronous and non blocking ?
  need to handle many simulataneous connection 
```js
const fs = require('fs')
fs.readFile('example.txt','utf-8',(err,data)=>{
 if(err)
 {
  console.log(err)
 }
})
console.log('Reading started... ')
```
`utf8` specifies that we want the data to be interpreted as a string

# Event Loop
- mechanism enables its asynchronous and non-clocking behavior.
- responsible for managing and processing various operations, including I/O operations, timers, and callbacks
- Phases
  1. TimersPhase 
  2. I/O callbacks phase
  3. Idle, Prepare phase - Internal phases not used by developers
  4. Poll Phase - Waits for events to be triggred
  5. Check Phase - exceutes `setImmediate`
  6. Close Callback - handles callbacks of resources that are closed. 

# Modules
enables to oragnize, encapsulate, and resuse code. 
Node.js uses CommonJS module system.
1. Creating Modules
```js
module.exports.add = (a,b)=> a+b
```
2. Exporting Module
`module.exports` object used to specify what should be available for other modules.
3. Built in Modules
```js
const fs = require('fs')
const os = require('os')
const path = require('path')
```
4. Core Modules vs Local Modules
core Modules : Built in modules
Local Modules: Modules we create in our project
5. NPM modules
external modules from Node Package Manager

# CommonJS Modules
module system
Synchronous
used for structuring and organizing code
define standardized way to create, import and use modules in as consistent manner.
role : `modularity`, `code reusablity`
Cachning: cached after first they are loaded. 
asynchronous loading using `require.async`

# NPM
- package Manager 
- Provides Central Repository
- Simplifies process of sharing, discovering and reusing code accross different project
1. Install
```js
npm i --save express
```
2. Updating Packages 
```js
npm update express
``` 
3. Publishing
```js 
npm publish
```
# EventEmitters
core modules in Node.js
implement custom event driven architecture
allows to emit event and register listerners
used for handling asynchronous events
1. Import
```js
const EventEmitter = require('events')
```
2. Creating Event Emitter
```js
const emitter = EventEmitter()
```
3. Emitting Events
```js
emitter.emit('event-name',arg1,arg2)
```
4.Listing to Events
```js
emitter.on('event-name',(arg1,arg2)=>{
  console.log(arg1,arg2)
})
```
5. Once Listener
`once` method to register listeners that are automatically removed
```js
emitter.once('event-name',()=>{
  console.log('This will run only once')
})
```
6. Removing Listener
To remove listerner for an event
`removeListener`, '`removeAllListner`
```js
emitter.removeListener('event-name',listenerFun)
emitter.removeAllListener('event-name')
```

# Streams
handling data flow
need to work with large amount of data 
allows data to processed piece by piece
benefits - reducing memory consumption and improving performance
Types
- Readable
- Writable
- Duplex
- Transform

# HTTP Module
inbuilt module, provides functionality for creating HTTP servers and making HTTP requests
Building `web applications`,`RESTful APIs`,`Network Communication`
```js
const http = require('http')
const server = http.createServer((req,res)=>{
  res.send('Welcome to Node.js')
})
const port = 3000
server.listen(port,()=>{
  console.log('server has been started')
})
```
`http request making` - also used to make HTTP requests to other servers or make API call of other server
```js
const http = require('http');

const options = {
  hostname: 'www.example.com',
  port: 80,
  path: '/path/to/resource',
  method: 'GET'
};

const req = http.request(options, (res) => {
  let data = '';

  res.on('data', (chunk) => {
    data += chunk;
  });

  res.on('end', () => {
    console.log(data);
  });
});

req.on('error', (error) => {
  console.error(error);
});

req.end();

```
# ExpressJS

# Callback Hell

# Error Handling

# Concurrency and Scaling

# fs

# http

# path

# os

# events

# util

# crypto

# stream
used to handle large data flow
allows to process data piece by piece
reducing node memory usage, Performance improvement
Types - `Writeable`,`Readable`,`Duplex`,`Transform`

# querystring

# url

# Modules and NPM

# Middleware
function exceuted sequentially
Type
- Global - application level middleware
- Route Specific - Route Specific middleware
eg. logging, authentication, validation

# Promises and Async/Await

# Clutser and Child Processes
allows to create child processes from single node.js process
help to use multiple cores and improve performance of your application
`ditributing workload`, `improve performance`

# Memory Management

# Security

# Debugging and Profiling

# Caching and Performance optimization

# websocket

# Authentication and Authorization

# Microservices

# Docker and Containerization

# GraphQL

# REST

# Kafka

# RabitMQ

# GRPC

# Serverless Architecture

# Testing and Test Automation

# Dependecy Injection

# Performance Monitoring and Profiling

# Internationalization

# Web Assembly

# Real Time Data Processing

# Hot Module Replacement

# Server Side Rendering

# Serverless Frameworks

# Service Workers

# Error Codes

# import vs require
|import|require|
|---|---|
|part of ES6 Modules| used to load Modules|
|used to import functionality and module|used to load modules|
|Asynchronous operation|Synchronous Operation|
|import specific functionality|load whole module|

# handling Errors in Node.js

callbacks - error as the first argument
Promises - try/catch

# Pyramid od Doom (nested Callbacks)
nested callbacks
unreadable code and complex to maintain
async.js, Promises, async/await

# Middleware
functions that are executed sequentially in order they are defined
task logging, authentication, data parsing
- global middleware - application level
- route specific middleware - applied to routes

# process.nextTick()
- useful for maintaining consistent behavior in asynchronous code
- ensures that piece of code runs immediately after the current operation completes
- used to defere the execution of a function until the next iteration

# garbage collection
automatic involves identifying and releasing memory that is no longer in use by the application
`v8 garbage collector` to manage memory

# Handling Sensitive Data
`ENV variables` - use Environment Variables
`configuration liabrary (dotenv)` - load configuration variables from the ENV files
`cloud services` - Built in mechanism to managing secrets

# Event Driven Architecture
- responding to events triggerd by user action or system event 
- fundamental aspect of Node.js
Built around non-blocking and asynchronous I/O 
eg. `user action` - network request, `file being read`

# Timers Module

# unhandledExceptions in Node.js

# module.export vs exports

# Node.js Child Process vs Threads

# cross site Scripting

# Handling of I/O operation asynchronously

# Purpose of util.promisify

# Module Resolution Process

# EventLoop Tick

# Handling Memory Leaks

# __dirname vs __filename

# Handling concurreny in Node.js

# Buffer Class

# require.cache

# Importance of `module` Object in Node.js

# Memory Intensive Task

# Writeable Stream

# Handling file uploads in Node.js

# process.argv vs process.env

# dns Module

# Handling HTTP requests and Responses in a Node.js

# require.resolve

# Global Object in Node.js and Difference with respective of Broswer Global Object

# util.inherits

# process.nextTick() vs setImmediate()

# Buffer Pool

# `process.nextTick()` method in relation to MicroTask

# URLSearchParams

# os.tmdir()

# implementing RESTful API using the express framework

# anonymous functions

