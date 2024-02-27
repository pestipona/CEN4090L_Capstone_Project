# Introduction to Node.js

Node.js is an open-source and cross-platform JavaScript runtime environment. It is a popular tool for almost any kind of project!

Node.js runs the V8 JavaScript engine, the core of Google Chrome, outside of the browser. This allows Node.js to be very performant.

A Node.js app runs in a single process, without creating a new thread for every request. Node.js provides a set of asynchronous I/O primitives in its standard library that prevent JavaScript code from blocking and generally, libraries in Node.js are written using non-blocking paradigms, making blocking behavior the exception rather than the norm.

When Node.js performs an I/O operation, like reading from the network, accessing a database or the filesystem, instead of blocking the thread and wasting CPU cycles waiting, Node.js will resume the operations when the response comes back.

This allows Node.js to handle thousands of concurrent connections with a single server without introducing the burden of managing thread concurrency, which could be a significant source of bugs.

Node.js has a unique advantage because millions of frontend developers that write JavaScript for the browser are now able to write the server-side code in addition to the client-side code without the need to learn a completely different language.

In Node.js the new ECMAScript standards can be used without problems, as you don't have to wait for all your users to update their browsers - you are in charge of deciding which ECMAScript version to use by changing the Node.js version, and you can also enable specific experimental features by running Node.js with flags.

# An Example Node.js Application

The most common example **Hello World** of `Node.js` is creating a **web server**:

```javascript
const http = require('node:http');

const hostname = '127.0.0.1';
const port = 3000;

const server = http.createServer((req, res) => {
    res.statusCode = 200;
    res.setHeader('Content-Type', 'text/plain');
    res.end('Hello World\n');
});

server.listen(port, hostname, () => {
    console.log(`Server running at http://${hostname}:${port}/`);
});
```

To run this snippet, save it as a `server.js` file and run `node server.js` in your terminal.

* `const http = require('node:http');` This line imports the [HTTP module](https://nodejs.org/api/http.html#http) from `Node.js`, allowing the **script** to **create a server** that can **accept HTTP requests**. 


* `const hostname = '127.0.0.1';` Defines the **hostname** where the **server will run**. in this case it is `127.0.0.1` which is the **loopback IP address**, referring to the **local machine**.


* `const port = 3000;` Sets the **port number** on which the **server** will **listen for requests**. `3000` is a common choice for **development environments**.


* `const server = http.createServer((req, res) => { ... });` Creates an **HTTP server**. The **function** passed to `createServer` is the **request handler**, called every time an **HTTP request** is made to the **server**. It takes two arguments:

  * `req` (request): An **object** containing **request details** (like URL, headers).
  * `res` (response): An **object** used to **return data back** to the **client**.


* Whenever a new request is received, the **request event** is called, providing **two objects**: a request (an `http.IncomingMessage` object) and a response (an `http.ServerResponse` object). Those 2 objects are essential to handle the **HTTP call**.

  * The `req` provides the **request details**. In this simple example, this is _not used_, but you could access the **request headers** and **request data**.

  * The `res` is used to **return data** to the **caller**.
 

* Inside the **request handler**:

  * `res.statusCode = 200;` Sets the **HTTP status code** of the **response** to `200`, indicating a **successful response**.

  * `res.setHeader('Content-Type', 'text/plain');` Sets the **HTTP header** of the **response**, specifying the **type of content** being **returned**, in this case, `plain text`.

  * `res.end('Hello World\\n');` **Ends** the **response process** and sends the string `Hello World` followed by a **newline character** as an argument to `end()` back to the **client**.


* `server.listen(port, hostname, () => { ... });` **Starts the server** and makes it **listen** on the **specified port** and **hostname**. The **callback function** is *executed*  `() => { ... }` once the **server is up and running**, **logging a message** to the **console** indicating that the server is running and listening for requests.

# More Topics on Node.js

* [Installing Node.js in Windows](./node/install-win.md)
* [What are Callback Functions in Node.js](./node/callbacks.md)
* [What are Promises in Node.js](./node/promises.md)