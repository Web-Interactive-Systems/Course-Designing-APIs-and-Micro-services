---
type: NoteCard
tags: []
---

# Lab - Working With Packages

In this unit we will practice working with packages in NodeJS.

## Prerequisites

* [ ] Basic knowledge of NodeJS and npm
* [ ] NodeJS installed on your machine
* [ ] A code editor (e.g. Visual Studio Code)


## Exercise 1: Project Setup

* [ ] Create an NPM project called `lab-nodejs-packages`
* [ ] The project sould have a main file: `src/index.js`
* [ ] A script `start` to run `src/index.js` usin node


## Exercise 2: Colorful Console.log

The goal of this exercise it to install and use a package to add colors to console.log. To do so we will use \`chalk\`.

* [ ] Explore the documentation of [chalk](https://github.com/chalk/chalk).
* [ ] Install chalk
* [ ] Import chalk
* [ ] Create a function `colorfulLogger` that takes two arguments: message (string to log in the console) and color (the color for the log)
* [ ] Test your code


## Exercise 3: Logger With Timestamp

The goal of this exercise it to install and use a package to add a timetamp to `colorfulLogger`. To do so we will use` date-fns`.

* [ ] Explore the documentation of [date-fns](https://github.com/date-fns/date-fns).
* [ ] Install date-fns
* [ ] Import date-fns
* [ ] Add a timestamp to your logger function using `date-fns` using this pattern 'yyyy-MM-dd HH'.
* [ ] Test your code


## Exercise 4: ASCII Art With Console.log

The goal of this exercise it to install and use a package to add ASCII art to `colorfulLogger`. To do so we will use figlet.

* [ ] Explore the documentation of [figlet](https://github.com/patorjk/figlet.js).
* [ ] Install figlet
* [ ] Import figlet
* [ ] Add a third argument to your logger function, `isAscii` if `isAscii` is `true` log using ascii art otherwise log using text.
* [ ] Test your code


