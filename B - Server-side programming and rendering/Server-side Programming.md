---
type: NoteCard
tags: []
---

# Server-side Programming

Content-rich and dynamic websites rely on server-side programming. This is a technology to deliver customized information in response to HTTP requests. Major websites use server-side programming.

For example, Google, Twitter, Facebook, and Amazon websites rely on millions of items stored on servers. As a user navigates these websites, the client communicates with servers to dynamically search, find, and render customized pages to the user.

Two argument to keep in mind:

1.  Content-rich websites can not run fully on the client-side, simply because the browser can not handle all the data needed by such web sites.
2.  In the same way, such websites can not be rendered fully as static web pages, simply because it is extremely difficult to render and store all the possible pages upfront on the server.

Other reasons for using server-side programming include security (e.g., storing sensitive data, passwords, and keys), performance (e.g., larger CPU and GPU processing units), interaction with other services (e.g., authenticating users, sending emails to users, etc.), and access to OS level functionalities (e.g., file system, etc.).

Thus, modern web apps use a combination of both: client and server-side programming.

## Static Versus Dynamic Content

A server can serve static and dynamic content.

*   Static content (e.g., a web page) is served as-is.
*   Dynamic content is processed (e.g., queried from a database), perhaps formated, personalized, and then served to the client.

## Server-side Frameworks

Like web frameworks React, Vue, Svelte, and others, there are server-side frameworks. They provide collections of functions and building blocks to solve common problems, speed up development, and simplify programming tasks for the server. For JS developer, NodeJS is one of the widely adopted framework for the server. Other more specialized frameworks on the top of Nodejs exist. Among these frameworks are ExpressionJS and SocketIO. Latter on, we will learn more about NodeJS, ExpressionJS, and SocketIO.

Keep in mind that a current trend is what is called meta-frameworks. In the JS jargon, meta-frameworks are frameworks that aim to provide one toolchain to build an app that has client-side and a server-side. Here parts of the code of the app that do not need web APIs will run on the server. The parts that need web APIs will run on the client. Among the meta-frameworks we have NextJS, NuxJS, and Astro. We will use Astro in one of our project.

Servers allow us to program many things, including access to IO (input-output), such as databases and file systems, HTTP request/response, socket communication, user authentication and authorization, session management, and templating.

## IO (Input-Output)

In computer-science, IO often refers to communicating with databases or file systems of the machine. In fact, a database is simply files that are stored on a machine, the files contains all the data that is started in a database. Server-side programming allow us to communicate with the IOs to store, modify, and retrieve information.

## HTTP Request/Response

HTTP stands for Hypertext Transfer Protocol. It is the computing protocol used to transfer data between a web server and a web browser. When you type a URL into your web browser and press enter, the browser sends an **HTTP request** to the server. Then, the server handles the request and responds with the requested resources. The response can be a web page, a JSON object, a string, etc.

Simply put, HTTP is a transportation system for data over the internet. By analogy, this is similar to a physical transportation system, such as railways and highways.

## Socket Communication

Socket communication is a way for two computers to establish a connection and communicate with each other over a network. It allows data to be sent and received between the two devices, enabling them to exchange information in real time.

In simpler terms, socket is like a phone call between two people. One person sends a message (data) to the other person, who then receives and responds to it. Similarly, in socket communication, one computer (socket) sends data to another computer's socket over a network connection. Socket works using events. A a socket can ***listen*** to receive events (messages) and can ***emit*** (sends) messages to others. Socket technology are mainly adequat for realtime communication and notification, such as chat messaging and video-conferencing.

## User Authentication and Authorization

User authentication and authorization help ensure control access to resources on a website or web application. User ***authentication*** is the process of verifying the identity a user. When a user wants to access a website or web application, they need to prove who they are. This is usually done by providing a username and password, but can also involve other methods like biometrics or two-factor authentication.

User ***authorization***, on the other hand, determines what actions a user can perform within the application once they have been authenticated. It involves setting permissions and access levels for different parts of the application based on the user's role or privileges. For example, an administrator might have full access to all features, while a regular user might only have permission to view certain pages or perform specific actions.

I summary, user authentication ensures that users are who they claim to be, while user authorization controls what actions they can perform within the application. By implementing these security measures, developers can safeguard their applications from unauthorized access and potential security breaches.

Information about the authentication and authorization of users are done in the server not in the browser. Imagine that all the passwords of the users are stored in a JavaScript variable of a web page, anyone can inpect the web page with a browser and see the passwords. Remember, the browser is not safeguarded and all sensitive operations should be performed in the server.

## Templating

Templating in server-side programming is a technique used to separate the structure of a web page from its content. It allows developers to create reusable templates that can be populated with dynamic data before being sent to the client's browser. For example, Twitter website has a top-bar, left-side bar, right-side bar, and feed view in the middle. The feed is more dynamic than the rest. Using templating, different parts of Twitter can be populated with their data and updated. Templating helps to maintain consistency in the design of a website and makes it easier to manage and update.

## Session Management

Session management in web development refers to the process of maintaining user sessions on a website or web application. A session is created when a user visits a website and ends when the user closes the browser, logs out, or the session expires. Using session management, a website can know which user is accessing what while the user navigates the website.

Session management can be implemented using various techniques. One common approach is using browser cookies to store session information. Cookies can be set, retrieved, and deleted using JavaScript.

For more secure session management, you may want to consider using server-side techniques, such as JSON Web Tokens (JWT) or sessions stored in a server.

## Benefits of Server-side Rendering

*   Efficient storage and processing of information
*   Personalized delivery of user experience
*   Control access and security
*   Session and state information
*   Notification and communication

