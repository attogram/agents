# Working with Rust

This document provides guidelines and best practices for AI agents working on Rust projects. Rust is a systems programming language focused on safety, speed, and concurrency. Its strict compiler enforces memory safety, which helps prevent many common bugs.

## 1. Core Concepts

- **Performance**: Rust is a compiled language that provides performance comparable to C and C++.
- **Memory Safety**: Rust's ownership system guarantees memory safety and thread safety at compile time. This means no null pointer dereferences, data races, or other common memory-related bugs.
- **Zero-Cost Abstractions**: High-level features in Rust are compiled down to efficient machine code, so you don't pay a performance penalty for using them.
- **Concurrency**: Rust's ownership and type system help you write concurrent code with confidence.

## 2. Development Environment

The Rust toolchain is managed by `rustup` and `cargo`.

- **`rustup`**: The Rust installer and version manager. It allows you to manage multiple Rust toolchains (e.g., stable, beta, nightly).
- **`cargo`**: The Rust build tool and package manager. It handles building your code, downloading dependencies, and running tests.
  - `cargo new <project_name>`: Creates a new Rust project.
  - `cargo build`: Compiles the project. Use `--release` for an optimized build.
  - `cargo run`: Compiles and runs the project.
  - `cargo test`: Runs the project's tests.
  - `cargo check`: Checks the code for errors without producing an executable. This is much faster than `cargo build`.
  - `cargo fmt`: Formats the code according to Rust's style guidelines.
  - `cargo clippy`: A linter that catches common mistakes and improves your code.

- **`Cargo.toml`**: The manifest file for a Rust project. It contains metadata and a list of dependencies (called "crates").

## 3. Ownership: The Core Feature

Ownership is Rust's most unique feature. It enables Rust to make memory safety guarantees without needing a garbage collector.

**The Rules of Ownership:**

1.  Each value in Rust has a variable that’s called its _owner_.
2.  There can only be one owner at a time.
3.  When the owner goes out of scope, the value will be dropped.

**References and Borrowing:**

- You can create references to a value, which allows you to access the value without taking ownership of it. This is called _borrowing_.
- You can have either one mutable reference (`&mut T`) or any number of immutable references (`&T`). You cannot have both at the same time. This prevents data races at compile time.

**Lifetimes:**

- Lifetimes are a way for the compiler to ensure that references are valid for as long as they need to be. For the most part, the compiler can infer lifetimes, but sometimes you need to annotate them explicitly.

## 4. Common Programming Concepts

- **Variables**: Declared with `let`. They are immutable by default. Use `mut` to make them mutable.
  ```rust
  let x = 5;
  let mut y = 10;
  ```
- **Structs**: A way to group related data together.
  ```rust
  struct User {
      username: String,
      email: String,
      active: bool,
  }
  ```
- **Enums**: A type that can be one of several different variants. `Option` and `Result` are two of the most important enums in the standard library.
  - `Option<T>`: Represents an optional value: either `Some(T)` or `None`.
  - `Result<T, E>`: Represents either success (`Ok(T)`) or failure (`Err(E)`).

- **Pattern Matching**: The `match` keyword is a powerful control flow construct that allows you to compare a value against a series of patterns and execute code based on which pattern matches.
  ```rust
  match some_option {
      Some(value) => println!("Got a value: {}", value),
      None => println!("Got nothing"),
  }
  ```

## 5. Error Handling

Rust uses the `Result<T, E>` enum for recoverable errors.

- Functions that can fail return a `Result`.
- The `?` operator is a convenient way to propagate errors. If the value of the `Result` is an `Ok`, the value inside the `Ok` will get returned from this expression, and the program will continue. If the value is an `Err`, the `Err` will be returned from the whole function as if we had used the `return` keyword.

```rust
use std::fs::File;

fn read_file() -> Result<String, std::io::Error> {
    let mut s = String::new();
    File::open("hello.txt")?.read_to_string(&mut s)?;
    Ok(s)
}
```

## 6. Testing

- Tests are functions annotated with the `#[test]` attribute.
- They are typically placed in the same file as the code they are testing, or in a `tests` directory.
- Run tests with `cargo test`.

```rust
pub fn add(a: i32, b: i32) -> i32 {
    a + b
}

#[cfg(test)]
mod tests {
    use super::*;

    #[test]
    fn it_works() {
        assert_eq!(add(2, 2), 4);
    }
}
```
