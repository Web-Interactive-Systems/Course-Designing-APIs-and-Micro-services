---
type: NoteCard
tags: []
---

# Lab - Middleware

The objective of this lab is to practice implementing an authentication middleware using Express.js. This middleware will use JWT to verify tokens from the request headers and populate the **`req.user`** object with user information if authentication is successful.

## Prerequisites

* [ ] Basic knowledge of NodeJS and npm
* [ ] NodeJS installed on your machine
* [ ] A code editor (e.g. Visual Studio Code)


## Exercise 1: Project Setup

* [ ] Create an NPM Project `lab-nodejs-express-json` `src/index.js` and `start` script


## Exercise 2: HTTP Server

* [ ] Create a server listening on port 5000


## Exercise 2: JWT

* [ ] Explore the documentation of [JWT](https://jwt.io/)
* [ ] Install jwt for nodejs (jsonwebtoken)


## Exercise 3: Middleware

* [ ] Complete the following middleware to authoticate the use using Bearer authorization


```js
// authenticationMiddleware.js
const jwt = require('jsonwebtoken');
const { UnauthenticatedError } = require('../errors');

const authenticationMiddleware = async (req, res, next) => {
    const authHeader = req.headers.authorization;

    if (...) {
        throw new UnauthenticatedError('No token provided');
    }

    const token = authHeader.split(' ')[1];

    try {
        const decoded = jwt.verify(token, process.env.JWT_SECRET);
        const { id, username } = decoded;
        
       // ....

    } catch (error) {
        throw new UnauthenticatedError('Not authorized to access this route');
    }
};
```

## Exercise 4: HTTP Server

* [ ] Create an http server with
  * [ ] \`login\` route
  * [ ] a protected \`dashboard\` route, meaning accessible only if authentication
* [ ] Add the middleware to the server


## Exercise 5: Testing the Server

