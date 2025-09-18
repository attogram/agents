# Working with Node.js

This document provides guidelines and best practices for AI agents working on Node.js projects. Node.js is a JavaScript runtime built on Chrome's V8 engine, allowing you to run JavaScript on the server side.

## 1. Core Concepts

- **V8 Engine**: Node.js executes JavaScript using the same high-performance V8 engine that powers Google Chrome.
- **Event-Driven, Non-Blocking I/O**: This is the cornerstone of Node.js. Instead of blocking a thread while waiting for an I/O operation (like reading a file or making a network request) to complete, Node.js registers a callback and continues executing other code. When the operation is finished, the callback is added to the event queue and executed by the event loop. This makes Node.js highly efficient for I/O-intensive applications.
- **The Event Loop**: Node.js uses a single-threaded event loop to handle all asynchronous operations. It continuously checks the event queue for new events and executes their associated callback functions.

## 2. Development Environment

- **npm (Node Package Manager)**: The default package manager for Node.js. It is used to install and manage project dependencies.
  - **`package.json`**: This file is the heart of any Node.js project. It contains metadata (name, version, etc.) and lists the project's dependencies (`dependencies` and `devDependencies`).
  - **`npm install`**: Installs all dependencies listed in `package.json`.
  - **`npm run <script-name>`**: Executes a script defined in the `scripts` section of `package.json`.

- **Modules (CommonJS)**: Node.js traditionally uses the CommonJS module system.
  - `require()`: Used to import a module.
  - `module.exports`: Used to export functions, objects, or values from a module.
    While ES Modules are now supported in modern Node.js, you will frequently encounter CommonJS in existing projects.

## 3. Core Modules

Node.js has a rich set of built-in modules. Here are a few essential ones:

- **`fs` (File System)**: Provides an API for interacting with the file system. Most of its methods have both synchronous and asynchronous (callback or promise-based) versions. Always prefer the async versions.

  ```javascript
  const fs = require("fs").promises;

  async function readFile() {
    const data = await fs.readFile("my-file.txt", "utf8");
    console.log(data);
  }
  ```

- **`http`**: The core module for creating HTTP servers and clients.

  ```javascript
  const http = require("http");

  const server = http.createServer((req, res) => {
    res.statusCode = 200;
    res.setHeader("Content-Type", "text/plain");
    res.end("Hello, World!");
  });

  server.listen(3000, "127.0.0.1", () => {
    console.log("Server running at http://127.0.0.1:3000/");
  });
  ```

- **`path`**: Provides utilities for working with file and directory paths in a cross-platform way.
  ```javascript
  const path = require("path");
  const fullPath = path.join("/foo", "bar", "baz/asdf", "quux", "..");
  // fullPath is '/foo/bar/baz/asdf'
  ```

## 4. Common Use Cases & Express.js

While the `http` module is powerful, most web servers in Node.js are built using a framework.

- **Express.js**: A minimal and flexible web application framework that provides a robust set of features for web and mobile applications. It simplifies tasks like routing, middleware, and handling requests and responses.

- **Basic Express Server**:
  ```javascript
  const express = require('express');
  const app = express();
  const port = 3000;

      app.get('/', (req, res) => {
        res.send('Hello World!');
      });

      app.listen(port, () => {
        console.log(`Example app listening at http://localhost:${port}`);
      });
      ```

  Node.js is also widely used for:

- **Building command-line interface (CLI) tools.**
- **Acting as the runtime for frontend build tools** like Webpack, Vite, and Parcel.
