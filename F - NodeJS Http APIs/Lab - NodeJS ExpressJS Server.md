---
type: NoteCard
tags: []
---

# Lab - NodeJS ExpressJS Server

In this unit will learn about ExpressJS. ExpressJS is an HTTP server. The goal is to handle resquests/responses between a client and a server.

## Prerequisites

* [ ] Basic knowledge of NodeJS and npm
* [ ] NodeJS installed on your machine
* [ ] A code editor (e.g. Visual Studio Code)


## Exercise 1: Project Setup

* [ ] Create an NPM project called `lab-nodejs-express-http`
* [ ] The project sould have a main file: `src/index.js`
* [ ] Add a script `start` to run `src/index.js` using **nodemon**


## Exercise 2: HTTP Server

ExpressJS is not a core module of NodeJS. We need to install it.

* [ ] Explore the documentation of [Expressjs](https://expressjs.com/) module.
* [ ] Install Expressjs
* [ ] Import import Expressjs
* [ ] Create a server listening on a 5000 port by following the hello-world example:
  * [ ] <https://expressjs.com/en/starter/hello-world.html>


## Exercise 3: HTTP Request/Response

* [ ] Add implement logic to handle different GET URLs requested by clients
* [ ] Use **`app.get(...)`** to determine the URL requested by the client
  * [ ] home page: \`url === '/'\`
  * [ ] about page: \`url === '/about'\`
  * [ ] other pages → not found page: 404
* [ ] Return html content
* [ ] Depending on the requested URL, send an appropriate response
    * [ ] For `/` and `/about` return an http status of \`200\` in adition to the content
    * [ ] For `not found` return an http status of \`400\` in adition to the content


## Exercise 4: Testing the Server

* [ ] Open your terminal or command prompt
* [ ] Start the server using npm command
* [ ] Open your web browser and navigate to [**`http://localhost:5000`**](http://localhost:5000)**`/`**
* [ ] You should see your home page content
* [ ] Try accessing [**`http://localhost:5000/about`**](http://localhost:5000/about) to see the "about page" content
* [ ] Accessing any other URL to see the "page not found" content


