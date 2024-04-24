---
type: NoteCard
tags: []
---

# How NodeJS Works

NodeJS use JavaScript Runtime. In computer science, a runtime means a sytem that executes (runs) some tasks or code. Here, runtime is the system that executes JavaScript code, which is V8 (see [[/notes/Introduction to NodeJS]]). This unit explains how NodeJS manages tasks using JS runtime.

## Two Types of Code in JS

In JS there are two types of code: (1) synchronous and (2) asychronous. Let us cover each.

### Sychronous Code

Sychronous code happen in order —instruction by instruction. Like in “realtime” for the sake of simplicity. Each synchronous instruction does not depend on any other OS or Network (e.g., HTTP) resources to complete. For example, the below `code` is synchronous:

```js
function add(a, b) { 
  return a + b; 
}

// add, when called, it happens in 'realtime' and the variable sum get the return which is 8. 
// Then the runtime moves to the next instruction, etc.
const sum = add(3, 5);

const n1 = 2;
const n3 = 4;

// same happens in 'realtime'
console.log('n1, n3 ', n1, n3);
```

The above code does not need any OS or Network resources to complete. It is synchronous. When synchronous code is run is runs in realtime.

### Asynchronous Code

Asynchronous code does not happen in realtime. By way of analogy, asynchronous code is similar to McDonald's. When we go to McDonald's to place an order, we don’t receive our order in realtime. We place the order and then wait for it to be completed (ready). Similarly, asynchronous code takes time to complete. For example, running a query to retrieve data from a database does not happen in realtime. It takes time to complete. So, we execute asynchronous code, but the operation will happen at a later time (asynchronously). This means, we execute the code and at a later time we get the results.

Therefore, an asynchronous operation requires us to write our code in a way to handle the results *when* the operation will be completed in the future (with success or failure).

Simply put, asynchronous code is a way to write code that does not wait for the results to complete *synchronousely* and resumes back when the results is completed. We will explore *how* to to so in JS code latter on.

### Non-blocking Event Loop

JS runs in one single thread, called event loop, as seen in [[/notes/Introduction to NodeJS]]. All the JS operations (code) needs to run in sequence in this event loop. The event loop is **non-blocking for asynchronous code**. This means that when a code is asynchronous, the event loop, will not stop and wait for the asynchronous operation to complete. Instead, the event loop will continue performing other operations and resumes asynchronous operations when completed. This is what makes the event loop of JS very efficient.

Keep in mind that event loop is **blocking** for synchronous code. Because synchronous code does not depend on blocking resources (OS, Network, etc.) it is generally very fast to execute. However, if we have, for example, a loop on handred of thousends of items, it will block the event loop. There are optimization techniques to avoid blocking the event loop with synchronous code, such as batch processing, but this is beyond the scope of this module.

Now, imagine if we have a **blocking** event loop for asynchronous code, each time we run an asynchronous operation, we stop until it complete. This will make JS useless. For example, all the web operations, such as buttons clicks, will freeze the page until they are completed.

Non-blocking event loop is a way to work with asynchronous code efficiently. When JS has an asynchronous operation it adds it to a queue of events and continues working on the next task. When the asynchronous operation is completed it resumes it using a callback.

## Asyhchnrous Techniques

There three asynchrous techniques in JS.

*   Callbacks
*   Promises
*   Async/await

### Callbacks

Functions in JS (and any other programming language) are meant to be called. A function is useless if it is *declared* and never *called*. There two ways to call a function. We can call a function explicitlly using \`()\`. Also, we can have another function call a function. A ***callback*** is a function that is passed as an argument to another function. This other function that takes a callback as an argument will then call the callback 👻. Here is an example:

```js
// cb is for saying callback
function callTheCallback(cb) {
  if(typeof callback === 'function') {
   // calling the callback
    cb('success', null); // notice: callTheCallback passes arguments into cb
  }
}

function myCB(status, error) {
  console.log('Do some work');
  console.log('Work status: ', status);
}

// calling callTheCallback which will then call myCB 
callTheCallback(myCB); // output: 
// Do some work
// Work status: success
```

This pattern of callbacks is the corner stone of asynchrouns code in JS. Basically, asynchrouns operations are registered with the work to be done (code) and a callback function to receive the results. When the asynchrouns operation is completed the callback is triggred (called) with the results as arguments.

Before async/await and promises (see below), callbacks were the main way to handle asynchronous code in NodeJS.

The order of arguments in a function is important. The callback function is the last parameter of the function.

```js
// Callback function is the last parameter
function(arg1, arg2, argN, callback) {
  // ...
}
```

Keep in mind that the the name of the function in your code or other APIs might not be called `callback`. It could be called `cb` or `done` or `next or resolve or reject`. The name of the function isn't important, but the order of the arguments is important.

Another challenge or the callbacks patterns is that there is no indication using some JS syntax that the function is asynchronous. A developer needs to know that the function is asynchronous by reading the documentation or reading the code.

#### Example of Callback

In the below example we read a file using NodeJS `fs` module.

```js
// Asynchronous example using a callback

// fs: file system module from NodeJS
import fs from 'fs';

// relative path to file
// the txt file contains: Content of the file.txt
const filePath = './notes/file.txt';

// callback
const callback = (error, data) => {
  if (error) {
    console.log('An error occurred...: ', error);
  } else {
    console.log(data); // Content of the file.txt
    console.log('Done!');
  }
};

// async request to read a file
//
// parameter 1: filePath
// parameter 2: encoding of utf-8
// parmeter 3: callback function
fs.readFile(filePath, 'utf-8', callback);

console.log("Last LINE of this js file...");
```

The results of the code

```bash
Last LINE of this js file...
Content of the file.txt
Done!
```

Notice “Last LINE of this js file...” is executed first because it synchronous.

We can also write the code without a named function:

```js
// async request to read a file
//
// parameter 1: filePath
// parameter 2: encoding of utf-8
// parmeter 3: callback function
fs.readFile(filePath, 'utf-8', (error, data) => {
  if (error) {
    console.log('An error occurred...: ', error);
  } else {
    console.log(data); // Content of the file.txt
    console.log('Done!');
  }
});
```

NodeJS has a set of APIs using asynchronous

```js
// Synchronous example without callback

import fs from 'fs';

const filePath = './note/file.txt';

try {
  // request to read a file, here we will wait until the read file is completed
  const data = fs.readFileSync(filePath, 'utf-8');
  console.log(data);
  console.log('Done!');
} catch (error) {
  console.log('An error occurred...: ', error);
}
```

## Asynchronous and Synchronous APIs in NodeJS

NodeJS provides both synchronous and asynchronous for some APIs. This is the case for File System module of NodeJS. Depending on the use cases, sometimes we don’t need asynchronous code. Meaning, the code will wait for the operation to complete. For example, if we are writing a JS script to read and write files (and there is no users waiting), we don’t need asynchronous code here. However, for server-side programming in the context of web or backend APIs use asynchronous code to avoid blocking the event loop.
