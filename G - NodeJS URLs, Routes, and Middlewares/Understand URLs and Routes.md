---
type: NoteCard
tags: []
---

# Understand URLs and Routes

Modern apps manage different data and resources. APIs resources are often accessed using unique URLs. For example, we can have these URLs

*   api/orders
*   api/products
*   …

### URL Path

A URL is an address that we enter into a client, like a browser, to locate a specific resource on the server. Knowing how the URLs works is important to organize APIs.

## Example of URL

```bash
http://localhost:5000/products/1?page=1&pageSize=20
```

The URL is follows a specific format:

```bash
scheme:[//authority]path[?query][#fragment]
```

| URL Part  | Example              | Explanation                                                                                                |
| --------- | -------------------- | ---------------------------------------------------------------------------------------------------------- |
| Scheme    | `https`              | The protocol used, such as `http`, `https`, `ftp`, `irc`, or `file`.                                       |
| Authority | `amazon.com`         | Consists of optional user info and a host, which is usually a domain name.                                 |
| Path      | `/products/1`        | Zero to many segments separated by a slash (`/`), specifying the resources.                                |
| Query     | `page=1&pageSize=20` | Optional part defined after the `?` character, consisting of parameter/value pairs to filter data further. |
| Fragment  | `sort=asc`           | Helps you be even more specific, such as sorting the data in a particular order.                           |

## HTTP Handlers

ExpressJS is a web framework that helps create HTTP APIs. ExpressJS helps create handlers to manage http requests/responses. Here is an example of code that handles HTTP requests for the URL `/products/1`:

```js
app.get('/products/:id', (req, res) => {
  // This the handler of this GET request `req.params.id`
})
```

The format of the handler is `app.<method>(<route>, <callback_handler>)`. The request for the route /products/1 with the GET method runs the code in the function which has access to the incoming request (req) and returns the response (res).

Another way to write the handler is:

```js
// callback_handler
const routeHandler = (incomingRequest, outgoingResponse) => {
  // This the handler of this GET request `incomingRequest.params.id`
}

app.get('/products/:id', routeHandler)
```

## Incoming Data

Sending data is an important part of HTTP. Data can be sent in three main ways in an HTTP request in several ways.

| Data            | Location                                                                     | Explanation                                                                                                                                                                                   |
| --------------- | ---------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Route parameter | `/products/:id`, where `:id` is the parameter                                | Route parameters are part of the URL.A route can have multiple parameters.They are used to identify a specific resources on the server.                                                       |
| Query parameter | `/products?page=1&pageSize=20`, where `?page=1&pageSize=20` is the parameter | Query parameters are part of the URL.A route can have multiple query parameters.They are used to filter data.                                                                                 |
| Request body    | `POST /products`                                                             | The request body is part of the HTTP request.It is used to send data to the API. The HTTP header indicates to the API the type of data, such as text, JSON, or binary (using *content-type*). |

## URL methods (Verbs)

Incoming data usually matches the CRUD methods based on the purpose of the action:

| Action | Method | Data Location              |
| ------ | ------ | -------------------------- |
| Create | POST   | Request body               |
| Read   | GET    | Route and query parameters |
| Update | PUT    | Request body               |
| Delete | DELETE | Route and query parameters |

## **Route parameter example with req.params**

If the request URL is `/products/3`. The Express route to handle this request is:

```js
// example 1
app.get('/products/:id', (req, res) => {
  // Notice req.params.id
  const id = req.params.id

    // ...
})

// example 2
app.get('/products/:toto', (req, res) => {
  // Notice req.params.toto
  const id = req.params.toto

    // ...
})
```

## **Query string example with req.query**

If the request URL is `/products?page=1&pageSize=5`. The Express route to handle this request is:

```js
app.get('/products', (req, res) => {
  // Notice req.query.page 
  const page = req.query.page
  // Notice req.query.pageSize
  const pageSize = req.query.pageSize

  // ...
})
```

## **Request body example with req.body**

If the request URL is `/products` and the request body is `{ "name": "Product 1" }`. The Express route to handle this request is:

```js
app.post('/products', (req, res) => {
  // Notice req.body.name
  const name = req.body.name

    // ...
})

// This require an helper from ExpressJS that parses JSON data in the request
```

