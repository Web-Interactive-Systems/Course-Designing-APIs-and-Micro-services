---
type: NoteCard
tags: []
---

# Lab - NodeJS HTTP Server

In this unit will learn about a native module of NodeJS called `http`. The HTTP module facilitates the creation of a web server. The goal is to handle resquests/responses between a client and a server.

Keep in mind that the HTTP module of NodeJS offers low level APIs, making the process of building servers and APIs harder and slow. There are other frameworks with more capabilities for NodeJS servers, such as ExpressJS, Hapi, Fastify, and Koa. We will be using ExpressJS because is widely used.

## Prerequisites

* [ ] Basic knowledge of NodeJS and npm
* [ ] NodeJS installed on your machine
* [ ] A code editor (e.g. Visual Studio Code)


## Exercise 1: Project Setup

* [ ] Create an NPM project called `lab-nodejs-http`
* [ ] The project sould have a main file: `src/index.js`
* [ ] A script `start` to run `src/index.js` usin **nodemon**


## Exercise 2: Http Server

Http module is a core module of NodeJS. There is no need to install it.

* [ ] Explore the documentation of [http](https://nodejs.org/api/http.html) module.
* [ ] Import http
* [ ] Create a server listening on a 5000 port


```js
const server = http.createServer((req, res) => {
  // Request handling logic will be implemented here
})

server.listen(5000, () => {
  console.log('Server is running on port 5000...')
})
```

## Exercise 3: Handling HTTP Resquest

* [ ] Inside the request handler function (**`createServer`** callback), implement logic to handle different URLs requested by clients
* [ ] Use **`req.url`** to determine the URL requested by the client
  * [ ] home page: \`url === '/'\`
  * [ ] about page: \`url === '/about'\`
  * [ ] not found page: 404
* [ ] Use { 'content-type': 'text/html' }
* [ ] Return html content
* [ ] Depending on the requested URL, send an appropriate response using **`res.writeHead()`** and **`res.write()`** methods
* [ ] End the response with **`res.end()`**


## Exercise 4: Testing the Server

* [ ] Open your terminal or command prompt
* [ ] Start the server using npm command
* [ ] Open your web browser and navigate to [**`http://localhost:5000`**](http://localhost:5000)
* [ ] You should see your home page content
* [ ] Try accessing [**`http://localhost:5000/about`**](http://localhost:5000/about) to see the "about page" content
* [ ] Accessing any other URL to see the "page not found" content


