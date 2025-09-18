# Working with TypeScript

This document provides guidelines and best practices for AI agents working on TypeScript projects. TypeScript is a statically typed superset of JavaScript that compiles to plain JavaScript. It helps in catching errors early during development and improves code quality and maintainability.

## 1. Core Concepts

- **Static Typing**: TypeScript's primary feature is static typing. This means you can declare the types of variables, function parameters, and return values. The TypeScript compiler will then check for type errors at compile time.
- **Superset of JavaScript**: Any valid JavaScript code is also valid TypeScript code. TypeScript adds type syntax on top of JavaScript.
- **Type Inference**: TypeScript can often infer the type of a variable even if you don't explicitly declare it.
- **Compilation**: TypeScript code is compiled to JavaScript using the TypeScript compiler (`tsc`). The output JavaScript can be configured to target different ECMAScript versions.

## 2. The `tsconfig.json` File

Every TypeScript project should have a `tsconfig.json` file. This file specifies the root files and the compiler options required to compile the project.

**Key Compiler Options:**

- `"target"`: Specifies the ECMAScript target version (e.g., `"ES2018"`, `"ESNext"`).
- `"module"`: Specifies the module code generation (e.g., `"CommonJS"`, `"ESNext"`).
- `"strict"`: Enables all strict type-checking options. It is highly recommended to keep this `true`.
- `"outDir"`: Redirect output structure to the specified directory.
- `"rootDir"`: Specifies the root directory of input files.

## 3. Basic & Complex Types

TypeScript provides a rich set of types.

- **Basic Types**: `string`, `number`, `boolean`, `null`, `undefined`, `any`, `unknown`, `void`.
  - Avoid using `any` as it opts out of type checking. Prefer `unknown` when the type is not known.

- **Arrays and Tuples**:
  - `string[]` or `Array<string>` for an array of strings.
  - `[string, number]` for a tuple (a fixed-length, fixed-type array).

- **Interfaces**: Used to define the shape of an object.

  ```typescript
  interface User {
    id: number;
    name: string;
    isActive?: boolean; // Optional property
  }
  ```

- **Type Aliases**: Create a new name for a type. Can be used for primitives, unions, intersections, etc.

  ```typescript
  type UserID = number | string;
  ```

- **Union Types (`|`)**: A variable that can hold more than one type.

  ```typescript
  let id: string | number;
  ```

- **Enums**: A way of giving more friendly names to sets of numeric values.
  ```typescript
  enum Direction {
    Up,
    Down,
    Left,
    Right,
  }
  ```

## 4. Functions

You can specify types for function parameters and return values.

```typescript
function greet(name: string): string {
  return `Hello, ${name}`;
}
```

## 5. Generics

Generics provide a way to create reusable components that can work over a variety of types rather than a single one.

```typescript
function identity<T>(arg: T): T {
  return arg;
}

let output = identity<string>("myString");
```

## 6. Development Workflow

- **Compilation**: Use `tsc` to compile your TypeScript code. You can run `tsc` in watch mode (`tsc -w`) to automatically recompile on file changes.
- **Execution**: For server-side applications, you can use a tool like `ts-node` to execute TypeScript code directly without a separate compilation step.
- **Linting**: Use ESLint with the `@typescript-eslint/parser` and `@typescript-eslint/eslint-plugin` packages to lint your TypeScript code.
