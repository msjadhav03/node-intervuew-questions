# NodeJS

### 1. What is Node.js?

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
