---
type: NoteCard
tags: []
---

# Lab - Async - Await

In this unit we will learn about async/await. Async/await is a newest way in JS to handle asynchronous operations. Async/await is syntactic sugar of promises. It makes asynchronous code looks like synchronous code. Thus, it is easier to read and maintain.

An `async function` declaration creates an async function object. Each time an async function is called, it returns a new promise will be resolved with the value returned by the async function, or rejected with an exception uncaught within the async function.

Async functions can contain zero or more `await` expressions. Await expressions make promise-returning functions behave as though they're synchronous by suspending execution until the returned promise is fulfilled or rejected.

The resolved value of the promise is treated as the return value of the await expression.

To use `await` we need to declare the enclosing block of code as `async`. Here is an example:

```js
// async keyword
async function logBooks() {
  // here we can use await
}
```

    async function logBooks() {
      const url = await doSomething();
      const res = await fetch(url);
      const data = await res.json();
      
      listOfBooks.push(data);

      console.log(listOfBooks);
    }

### **Top-level async/await**

The most recent versions of Node.js added top-level async/await for ES6 modules. You need to add a property named `type` in the **package.json** with a value of `module` to use this feature.

```js
// package.json
{
    "type": "module"
}
```

Using top-level await in NodeJS, we can use await outside `async` block.

```js
// top-level async/await asynchronous example

const fs = require('fs').promises;

const filePath = './file.txt';

// `async` before the parent function
try {
  // `await` before the async method
  const data = await fs.readFile(filePath, 'utf-8');
  console.log(data);
  console.log('Done!');
} catch (error) {
  console.log('An error occurred...: ', error);
}
console.log("I'm the last line of the file!");
```

