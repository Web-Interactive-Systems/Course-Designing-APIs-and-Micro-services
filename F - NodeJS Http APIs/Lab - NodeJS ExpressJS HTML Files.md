---
type: NoteCard
tags: []
---

# Lab - NodeJS ExpressJS HTML Files

In this unit will learn about serving HTML pages to the client using ExpressJS.

## Prerequisites

* [ ] Basic knowledge of NodeJS and npm
* [ ] NodeJS installed on your machine
* [ ] A code editor (e.g. Visual Studio Code)


## Exercise 1: Project Setup

* [ ] Create an NPM project called `lab-nodejs-express-html`
* [ ] The project sould have a main file: `src/index.js`
* [ ] Create folder called `pages` inside `src `folder
* [ ] Add a script `start` to run `src/index.js` using **nodemon**


## Exercise 2: HTTP Server

* [ ] Create a server listening on port 5000


## Exercise 3: HTTP Request/Response

* [ ] Add `index.html` and `about.html` and `400.html` pages with some content inside the folder `pages`
* [ ] Add implement logic to handle different GET URLs requested by clients into your server
* [ ] Use **`app.get(...)`** to determine the URLs
* [ ] Use the code below to send the appropriate file to the client depending on the URL


```js
// for `/` URL, we serve the index.html

res.sendFile(path.resolve(__dirname, './pages/index.html'));
```

## Exercise 4: Testing the Server

* [ ] Open your terminal or command prompt
* [ ] Start the server using npm command
* [ ] Open your web browser and navigate to [**`http://localhost:5000`**](http://localhost:5000)**`/`**
* [ ] You should see your home page content
* [ ] Try accessing [**`http://localhost:5000/about`**](http://localhost:5000/about) to see the "about page" content
* [ ] Accessing any other URL to see the "page not found" content


