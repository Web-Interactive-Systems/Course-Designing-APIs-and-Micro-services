---
type: NoteCard
tags: []
---

# NodeJS APIs Middlewares

In this unit we will learn about processing requests. Sometimes, when we have an HTTP request, we might need to process it. For example, it is common to process requests to authenticate users, log information about requests, add new information to the responses, etc.

Here is a logger example:

```js
const logger = (req, res, next) => {
  const method = req.method;
  const url = req.url;
  const time = new Date().getFullYear();

  console.log(method, url, time);

  next(); // a callback
}
```

This logger will get a request and log method, url and timestamp in the console.

## Handling Requests

Handling a request is a series of steps. For example, if the user needs to be logged in to access a resource, the steps might look like this:

Preprocessing: to determine that the user sent the proper credentials (optional)

Processing: talk to some kind of data source, like a database or an API endpoint

Postprocessing: run code after the request is complete (optional)

ExpressJS works using this pattern, and it is known as middleware.

## ExpressJS Middleware

A middleware is an interceptor. It gets the request, do the processing, and chain to other middlewares.

```js
//  req => middleware => res
```

ExpressJS middlewares are implemented using the `use` function.

```js
app.use((req, res, next) => {})
```

*   req: is the request
*   res: is the response
*   next: is a callback to chaine to other middlewares

If the `next()` function isn't called, processing of the request stops at the current middlewares.

## Using A Middleware

```js
// a middleware at the beginning
app.use((req, res, next) => {
  // Pre request
})

app.get('/protected-resource', () => {
  // Handle the actual request
})

// another middleware
app.use((req, res, next) => {
  // Post request
})

app.get('/login', () => {})
```

To use, for example, the logger middleware defined above,

```js
// middleware
app.use(logger);

// ...
```

