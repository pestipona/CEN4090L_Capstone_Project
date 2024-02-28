# Introduction to Express

**Express** is a minimal and flexible `Node.js` **web application framework** that provides a robust set of features for web and mobile applications. 

Express is designed to be simple and easy to use. By providing a thin layer of fundamental web application features, it allows developers to build applications quickly without losing the power of Node.js.

Express applications essentially comprise a series of middleware function calls. Middleware functions can execute code, make changes to the request and response objects, end the request-response cycle, and call the next middleware function in the stack. This makes Express very flexible and allows developers to easily add functionalities like session management, error handling, and more.

Express provides a sophisticated routing mechanism that allows for the management of different HTTP routes via a simple and intuitive API. Developers can define routes based on HTTP methods and URLs, organize route logic, and create route handlers with different verbs.

**APIs:** Express is widely used to build RESTful APIs that serve JSON data to clients.

**Web Applications:** It can be used to serve web pages, templates, and static files, making it suitable for full-fledged web application development.

**Integration with Front-End Frameworks:** Express easily integrates with front-end frameworks (like Angular, React, or Vue.js) to develop full-stack applications by serving as the backend API layer.

`Express` is built on `Node.js`, so you need Node.js

# Installing Express

Assuming you’ve already installed `Node.js`, create a directory to hold your application, and make that your working directory.

```text
$ mkdir myapp
$ cd myapp
```

Use the `npm init command `to create a package.json file for your application. For more information on how package.json works, see [Specifics of npm’s package.json handling](https://docs.npmjs.com/files/package.json).

```text
$ npm init
```

This command prompts you for a number of things, such as the name and version of your application. For now, you can simply hit RETURN to accept the defaults for most of them, with the following exception:

```text
entry point: (index.js)
```

Enter `app.js`, or whatever you want the name of the main file to be. If you want it to be `index.js`, hit RETURN to accept the suggested default file name.

Now install **Express** in the `myapp` directory and save it in the **dependencies** list using the following command.

```text
$ npm install express
```

# Express Hello World Example

he most common example **Hello World** of `Express` is creating a **web server**:

```javascript
const express = require('express');

const app = express();
const port = 3000;

app.get('/', (req, res) => {
    res.send('Hello World!');
});

app.listen(port, () => {
    console.log(`Example app listening on port ${port}`);
});
```

To run this snippet, save it as a `index.js` file and run `node index.js` in your terminal.

* `const express = require('express');` this line **imports** the `Express` **library** into the file, allowing the developer to use its **features** to **create a web server**. The `require` function is used to **load modules** in `Node.js`.


* `const app = express();` this line **creates an instance** of an **Express application**. It is through the object `app` that you can start **setting up your server**, such as **defining routes** and **listening for requests**.


* `const port = 3000;` this line sets the **port number** on which your **Express server** will **listen**. Port `3000` is commonly used for **development environments**.


* `app.get('/', (req, res) => {...}` this line **defines** a **route handler** for **GET requests** to the **root URL** (`/`). Whenever a **GET request** is made to the **root** of your **server**, the **function** passed as the **second argument** will be **executed**.
  * `req` (short for request) is an **object** containing information about the **HTTP request** that **triggered** the **route**.
  * `res` (short for response) is an **object** that allows you to **manipulate** the **HTTP response** that your **server** will **send back** to the **client**.


* `res.send('Hello World!');` inside the **route handler**, this line **sends a response** back to the **client** with the **text** `Hello World!`. This is what the **client** will see when they **navigate** to the **root URL** of your **server**.


* `app.listen(port, () => {...}` this line tells your **Express app** to **start listening** for **incoming requests** on the **specified port** (`3000` in this case). When the server successfully starts listening on that port, the **callback function** passed as the **second argument** is **executed**.

  * `console.log(Example app listening on port ${port});` this **line is executed** once the **server starts listening** on the **specified port**. It **logs a message** to the **console** indicating that the **server is up and running** and **listening on port 3000**.

# Other Express Topics:

* [Express-Generator](./express-generator.md)
* [Express Routing](./express-routing.md)