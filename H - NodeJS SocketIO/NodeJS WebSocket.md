---
type: NoteCard
tags: []
---

# NodeJS WebSocket

The need for real-time web apps has increased in the last decade. HTTP communication between a client and browser can qualified as unidirectional. When a user interacts with a web app, the client (browser) always triggers communication to a server. A client sends a request for a web page and waits for a response. This unidirectional communication is unsuitable for real-time when both a client and a server must send and receive data to each other at the same time.

Like HTTP, socket technology has two parts: a client and a server.

## Polling

One technique to remediate the unidirectionality of HTTP is polling when the browser polls data from a server at regular intervals. However, polling can be insufficient because of the HTTP traffic involved.

    function pollData() {
       // ...
    }

    setTimeout(pollData, 5000);

## Bidirectional Channel

WebSocket protocol enables an efficient bidirectional communication channel. It keeps an open connection between a server and a client.

## Advantages of WebSocket

*   Bidirectional communication with true concurrency
*   Low latency
*   Low bandwidth
*   Works over TCP (uses HTTP only during handshake)
*   Supports most browsers including mobile

## Initializing Connection

WebSocket connection requires a URL to establish a connection with the server.

    // unsecure connection
    const ws = new WebSocket('ws:localhost:5000')

    // secure connection
    const wss = new WebSocket('wss:localhost:5000')

## Listening for Events

Once a connection is established, webSocket (ws) can listen for events. Events that ws fires are:

*   open: When a connection with ws is opened
*   message: When data is received through ws
*   error: When the connection is closed due to an error
*   close: When the connection is closed

Listening for these events can be done in the same manner as DOM elements events: either using on `ws.on${event_name}` or `ws.addEventListener(${event_name})`

    // These are equivalent

    ws.addEventListener("error", (event) => {});

    ws.onerror = (event) => {};

## Sending Data to Server

WebSocket offers the \`send\` method to send data to the server. Data can be text, Blob, or ArrayBuffer.

However, because establishing a connection is asynchronous and prone to failure, we should ensure sending data only when the connection has opened.

    ws.onopen = (event) => {
      const msg = "A text message to the server!"
      ws.send(msg);
    }

Interestingly, `ws` can communicate using JSON, by encoding it into a string (JSON.stringify(json\_object)) and parsing it as JSON (JSON.parse(json\_string)).

## WebSocket Frameworks

Like modern web frameworks, there are a number of frameworks that facilitate working with WebSocket. SocketIO has a huge user base.

