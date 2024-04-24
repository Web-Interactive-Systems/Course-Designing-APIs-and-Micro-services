---
type: NoteCard
tags: []
---

# Lab - Callbacks

In this unit we will learn about callbacks. Callbacks are an essential concept in JavaScript and NodeJS, particularly when dealing with asynchronous operations. In NodeJS, many operations, such as file reading, network requests, and database queries, are **non-blocking** and **asynchronous** by default. Callbacks provide a way to handle these asynchronous operations and execute code after the operation completes.

## What is a Callback?

A callback is function that is passed as an argument to another function.

## Example: A Basic Callback

One way to simulate asynchronous operations is using the function setTimeout. SetTimeout will delay the execution of the code until a a time-delay (in milisiconds) is . This is like setting a timer on a smartphone, when the timer is done we get notified. Here the notification will be running the code.

```js
function greet(name, callback) {
    setTimeout(() => {
        callback(`Hello, ${name}!`);
    }, 1000); // Simulating asynchronous operation
}

// Calling the greet function with a callback
greet("Alex", (message) => {
    console.log(message);
});

// Similary to
const cb = (message) => {
    console.log('Another way ', message);
};

const name = 'Sara';

// cb is just an argument
greet(name, cb);
```

## Exercise: Callback Hell

Callback hell refers the nesting of callbacks. This can be harder to follow and there are new ways to avoid nesting using async/await or promises.

Write three functions each takes a callback. The functions can be nested and run in sequence to show the following:

```js
Step 1 completed.
Step 2 completed.
Step 3 completed.
All steps completed.
```

Here is a starter:

```js
step1(() => {
    step2(() => {
        step3(() => {
            // ...
        });
    });
});
```

## Exercise: User Authentification

Write a function `login` that takes username, password, and callback as arguments. The function should check:

*   if username equals “toto” and password equals “superSecure”

    *   then, returns `null` as first argument and `“Success”` as a second argument in the callback

*   otherwise

    *   returns `”Invalid ``credentials”` in the callback

Here is a starter

```js
// Using the login function
login(..., ..., function(...) {
    if (err) {
        
    } else {
        
    }
});
```

