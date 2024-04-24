---
type: NoteCard
tags: []
---

# Backend APIs

In this unit we will learn about creating backend APIs in NodeJS.

## What is an API?

An API, or Application Programming Interface, is a set of rules and protocols that allows different applications or systems to communicate with each other. An API defines the ways and data formats that applications can use to request and exchange information. Here we will focus on web APIs.

## Types of Web APIs

There are two main web APIs **backend APIs and third-party APIs**.

1.  **Backend APIs:** These APIs are used to enable communication between the frontend (client-side) and the backend (server-side) of an application. They allow clients to request data or perform actions on the server.
2.  **Third-party APIs:** These are APIs provided by external services or platforms, allowing developers to access their functionality or data. For example, media APIs (like Twitter or Google) provide access to data and functionalities.

## Key Concepts of Web APIs

Some of the main concepts of web APIs are:

### Endpoints

APIs consist of endpoints, which are specific URLs that clients can interact with to perform certain actions or retrieve data. Each endpoint typically corresponds to a specific function or resource on the server.

### HTTP Methods

APIs use HTTP methods (such as GET, POST, PUT, DELETE) to specify the type of action the client wants to perform on the server. For example, GET is used to retrieve data, POST is used to submit data, PUT is used to update data, and DELETE is used to delete data.

### Request and Response

When a client makes a request to an API endpoint, it sends a request containing information such as the HTTP method, headers, and optional data (in the case of POST or PUT requests). The server then processes the request and sends back a response containing the requested data or indicating the outcome of the request (e.g., success or failure).

### Data Formats

APIs typically use data formats like JSON (JavaScript Object Notation) or XML (eXtensible Markup Language) to structure the data being exchanged between the client and server. JSON is the most commonly used format due to its simplicity and lightweight nature.
