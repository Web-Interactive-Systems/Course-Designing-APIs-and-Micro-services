---
type: NoteCard
tags: []
---

# Lab - Promises

In this unit we will learn about Promises in JavaScript. A promise is an *object* representing the eventual completion or failure of an asynchronous operation. This like the recit that we get when order something from Mackdonald’s.

The promise object is like the receipt that we get when we order something from McDonald's. Later, we use our receipt to pick up the order.

Most of the time we use already-created promises, provided by other APIs. Let us focus first on using promises.

Promise is a simpler way of using callback to handle asynchronous code. Here is an example of a `compressFileAsync`.

First using callbacks:

```js
function successCallback(result) {
  console.log(`file ready at URL: ${result}`);
}

function failureCallback(error) {
  console.error(`Error compressing file: ${error}`);
}

function compressFileAsync(settings, function (result) {
  // successCallback
}, function (error) {
  // failureCallback
});
```

To compress a file

```js
createAudioFileAsync(settings, successCallback, failureCallback)
```

Promises allow us to call createAudioFileAsync using this way:

```js
createAudioFileAsync(settings)
  .then(successCallback, failureCallback);
```

The only difference is that the callbacks for sucess and failure are ***attached*** to the main asynchronous function. This attachement is done using \`then\` (to get the success result) or \`catch\` (to get the failure result).

## Chaining

Callbacks nesting (callback hell) is harder to read and maintain.

```js
// example of callback hell
doSomething(function (result) {
  doSomethingElse(result, function (newResult) {
    doThirdThing(newResult, function (finalResult) {
      console.log(`Got the final result: ${finalResult}`);
    }, failureCallback);
  }, failureCallback);
}, failureCallback);
```

Promises provide a way to nest asynchronous function using `then` and `catch`, like this:

```js
const promise = doSomething();
const promise2 = promise.then(successCallback, failureCallback);
```

Or

```js
doSomething()
  .then(function (result) {
    return doSomethingElse(result);
  })
  .then(function (newResult) {
    return doThirdThing(newResult);
  })
  .then(function (finalResult) {
    console.log(`Got the final result: ${finalResult}`);
  })
  .catch(failureCallback);
```

Or using arrow function

```js
doSomething()
  .then((result) => doSomethingElse(result))
  .then((newResult) => doThirdThing(newResult))
  .then((finalResult) => {
    console.log(`Got the final result: ${finalResult}`);
  })
  .catch(failureCallback);
```

Each promise represents the completion of one asynchronous step in the chain.

The arguments to `then` are optional. The next promise in the chain get the return of the previous promise.

The `catch(failureCallback)` is short for `then(null, failureCallback)`.

The `doSomethingElse` and `doThirdThing` can return any value. If they return promises, that promise is first waited until it settles, and the next callback receives the fulfillment value, not the promise itself.

It is important to always return promises or values in `then` callbacks, even if the promise resolves to `undefined`.

## Promises Return

If the previous handler started a promise but did not return it, there's no way to track its settlement anymore, and the promise is said to be "floating".

Here is an example

    doSomething()
      .then((url) => {
        // Missing `return` keyword in front of fetch(url).
        fetch(url);
      })
      .then((result) => {
        // result is undefined, because nothing is returned from the previous
        // handler. There's no way to know the return value of the fetch()
        // call anymore, or whether it succeeded at all.
      });

Here the right way

    doSomething()
      .then((url) => {
        // `return` keyword added
        return fetch(url);
      })
      .then((result) => {
        // result is a Response object
      });

By returning the result of the `fetch` call (which is a promise), we can both track its completion and receive its value when it completes.
