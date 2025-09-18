# Working with JavaScript

This document provides guidelines and best practices for AI agents working on JavaScript projects. As the most widely used programming language, a strong understanding of modern JavaScript is essential.

## 1. Core Concepts (ES6+ and beyond)

Modern JavaScript (ECMAScript 2015 and later) introduced many features that are now standard practice.

- **`let` and `const`**: Always prefer `const` for variables that will not be reassigned. Use `let` for variables that will be reassigned. Avoid using `var` to prevent issues with hoisting and function-level scope.
- **Arrow Functions**: Use arrow functions (`=>`) for more concise function syntax, especially for anonymous functions and to maintain the lexical `this` context.
  ```javascript
  const add = (a, b) => a + b;
  ```
- **Promises and `async/await`**: These are the standard for handling asynchronous operations. See the "Asynchronous JavaScript" section below for more details.
- **Template Literals**: Use backticks (`` ` ``) for string interpolation and multi-line strings.
  ```javascript
  const name = "Jules";
  const greeting = `Hello, ${name}!`;
  ```
- **Destructuring**: A convenient way to extract properties from objects or elements from arrays.
  ```javascript
  const { name, age } = userObject;
  const [first, second] = anArray;
  ```
- **Spread and Rest Syntax (`...`)**:
  - **Spread**: Expands an iterable (like an array or object) into individual elements.
  - **Rest**: Collects multiple elements into a single array.

## 2. Development Environment

A robust development environment is key to writing high-quality code.

- **Node.js & npm/yarn**: Most JavaScript projects, even frontend ones, use Node.js as a runtime for build tools. `npm` (Node Package Manager) or `yarn` are used to manage project dependencies, which are defined in `package.json`.
- **Linters (ESLint)**: Use ESLint to statically analyze your code to quickly find problems. It should be configured with a standard style guide (like Airbnb's) and project-specific rules in an `.eslintrc` file.
- **Formatters (Prettier)**: Use Prettier for automatic code formatting. This ensures a consistent code style across the project. It should be configured with an `.prettierrc` file.

## 3. Asynchronous JavaScript

JavaScript is single-threaded, so understanding how to handle asynchronous operations without blocking the main thread is critical.

- **Callbacks**: The original way to handle async operations. They are functions passed as arguments to other functions, to be executed later. Prone to "callback hell" (deeply nested callbacks).
- **Promises**: A more robust solution. A Promise is an object representing the eventual completion (or failure) of an asynchronous operation. Use `.then()` for success, `.catch()` for errors, and `.finally()` for cleanup.
- **`async/await`**: Syntactic sugar on top of Promises that makes asynchronous code look and behave more like synchronous code, which is much easier to read and maintain. This is the preferred method for modern JavaScript.

  ```javascript
  async function fetchData(url) {
    try {
      const response = await fetch(url);
      if (!response.ok) {
        throw new Error(`HTTP error! status: ${response.status}`);
      }
      const data = await response.json();
      return data;
    } catch (error) {
      console.error("Fetch failed:", error);
    }
  }
  ```

## 4. Modules

Modern JavaScript uses ES Modules (ESM) for code organization.

- **ES Modules (`import`/`export`)**: The standard module system for the browser and modern Node.js.
  - `export`: Used to export functions, objects, or primitives from a given file.
  - `import`: Used to import live bindings from an exported module.

  ```javascript
  // lib.js
  export const PI = 3.14;
  export default function sayHello() {
    console.log("Hello!");
  }

  // main.js
  import sayHello, { PI } from "./lib.js";
  console.log(PI);
  sayHello();
  ```

- **CommonJS (`require`/`module.exports`)**: The legacy module system used in Node.js. You will still encounter this in older projects.

## 5. Testing

- **Frameworks**: [Jest](https://jestjs.io/) is a very popular, all-in-one testing framework. Other popular choices include [Mocha](https://mochajs.org/) (a test runner) and [Chai](https://www.chaijs.com/) (an assertion library).
- **Running Tests**: Tests are typically run from the command line via a script in `package.json`, for example: `npm test`.
- **Assertions**: Tests should make clear assertions about the expected behavior of the code. For example, `expect(add(1, 2)).toBe(3);` in Jest.
