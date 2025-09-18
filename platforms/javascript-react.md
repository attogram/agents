# Working with React

This document provides guidelines and best practices for AI agents working on React projects. React is a JavaScript library for building user interfaces, developed by Facebook.

## 1. Core Concepts

- **Components**: The fundamental building blocks of React applications. A component is a self-contained, reusable piece of UI. Modern React uses **functional components**.
  ```jsx
  function Welcome(props) {
    return <h1>Hello, {props.name}</h1>;
  }
  ```
- **JSX (JavaScript XML)**: A syntax extension for JavaScript that allows you to write HTML-like markup inside a JavaScript file. It is not required to use React, but it is the standard and recommended way.
  ```jsx
  const element = <h1>Hello, world!</h1>;
  ```
- **Props (Properties)**: Read-only data that is passed from a parent component to a child component.

  ```jsx
  // Usage in parent
  <Welcome name="Jules" />;

  // Access in child
  function Welcome(props) {
    // props.name is "Jules"
    // ...
  }
  ```

- **State**: Data that is managed within a component. When a component's state changes, React re-renders the component. State is managed using the `useState` hook in functional components.

## 2. Hooks

Hooks are functions that let you "hook into" React state and lifecycle features from functional components.

- **`useState`**: The most common hook. It allows you to add state to a functional component. It returns a stateful value and a function to update it.

  ```jsx
  import { useState } from "react";

  function Counter() {
    const [count, setCount] = useState(0); // 0 is the initial state

    return (
      <div>
        <p>You clicked {count} times</p>
        <button onClick={() => setCount(count + 1)}>Click me</button>
      </div>
    );
  }
  ```

- **`useEffect`**: Lets you perform side effects in functional components. Side effects can include data fetching, subscriptions, or manually changing the DOM. The function passed to `useEffect` will run after the render is committed to the screen.

  ```jsx
  import { useState, useEffect } from "react";

  function Example() {
    const [data, setData] = useState(null);

    useEffect(() => {
      // This effect runs once, after the initial render
      fetch("https://api.example.com/data")
        .then((response) => response.json())
        .then((data) => setData(data));
    }, []); // The empty dependency array means this effect runs only once
  }
  ```

- **`useContext`**: Allows you to subscribe to React context without introducing nesting. It's a way to share state across the entire app without having to pass props down manually at every level (prop drilling).

## 3. Conditional Rendering

You can use standard JavaScript operators like `if` or the conditional (ternary) operator to create distinct elements depending on the state.

```jsx
function Greeting(props) {
  const isLoggedIn = props.isLoggedIn;
  if (isLoggedIn) {
    return <UserGreeting />;
  }
  return <GuestGreeting />;
}
```

You can also use the logical `&&` operator for shorter syntax:

```jsx
<div>
  {unreadMessages.length > 0 && (
    <h2>You have {unreadMessages.length} unread messages.</h2>
  )}
</div>
```

## 4. Handling Events

Handling events with React elements is very similar to handling events on DOM elements. React events are named using camelCase, and with JSX you pass a function as the event handler, rather than a string.

```jsx
<button onClick={handleClick}>Click me</button>
```

## 5. Development Environment

- **Create React App (`CRA`)**: The traditional way to set up a new single-page React application. It provides a modern build setup with no configuration.
  ```bash
  npx create-react-app my-app
  ```
- **Vite**: A modern and much faster alternative to CRA for starting new React projects. It uses native ES modules in the browser during development.
  ```bash
  npm create vite@latest my-react-app -- --template react
  ```
