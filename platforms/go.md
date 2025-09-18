# Working with Go

This document provides guidelines and best practices for AI agents working on Go projects. Go is a statically typed, compiled language known for its simplicity, performance, and excellent support for concurrent programming.

## 1. Development Environment

Go has a strong focus on tooling and a standardized project structure.

### Go Modules

Modern Go projects use Go Modules to manage dependencies. A project is defined as a module, and it's declared with a `go.mod` file in the project's root directory.

- **`go.mod`**: This file defines the module's path (its name), the version of Go it was built with, and its dependencies.
- **`go.sum`**: This file contains the checksums of the direct and indirect dependencies to ensure reproducible builds. It is automatically generated and updated.

### The `go` command

The `go` command is the main entry point for a suite of tools.

- `go run <file.go>`: Compiles and runs a Go program.
- `go build`: Compiles the packages and their dependencies.
- `go test`: Runs tests.
- `go fmt`: Formats Go source code according to the language's conventions. This should be run frequently.
- `go get <package>`: Adds a new dependency to the current module.
- `go mod tidy`: Ensures the `go.mod` file matches the source code's dependencies, adding any missing ones and removing unused ones.

## 2. Basic Syntax

- **Packages**: Every Go program is made up of packages. The `main` package is the entry point for an executable program.
- **Variables**:
  - `var name string = "Jules"`: Declares a variable with its type.
  - `name := "Jules"`: The `:=` syntax is shorthand for declaring and initializing a variable. Go infers the type.
- **Structs**: A `struct` is a collection of fields. It's used to group data together.
  ```go
  type User struct {
      ID   int
      Name string
  }
  ```
- **Functions**: Functions can take zero or more arguments and can return multiple values.
  ```go
  func add(a int, b int) int {
      return a + b
  }
  ```

## 3. Key Language Features

### Concurrency (Goroutines and Channels)

Go's approach to concurrency is one of its most powerful features.

- **Goroutines**: A goroutine is a lightweight thread managed by the Go runtime. You can start a new goroutine with the `go` keyword.
  ```go
  go myFunction() // This will run myFunction concurrently.
  ```
- **Channels**: Channels are a typed conduit through which you can send and receive values with the channel operator, `<-`. They are the primary way to communicate between goroutines.

  ```go
  messages := make(chan string)

  go func() { messages <- "ping" }()

  msg := <-messages
  fmt.Println(msg) // "ping"
  ```

### Interfaces

Interfaces in Go provide a way to specify the behavior of an object. An interface is a collection of method signatures. A type implements an interface by implementing its methods. There is no `implements` keyword; the implementation is implicit.

```go
type Shape interface {
    Area() float64
}
```

### Error Handling

Go has a simple, idiomatic approach to error handling. Functions that can fail return an `error` value as their last return value.

```go
f, err := os.Open("filename.ext")
if err != nil {
    log.Fatal(err)
}
// do something with the file f
```

## 4. Testing

Go has a built-in testing framework provided by the `testing` package.

- Test files are named `*_test.go`.
- Test functions are named `TestXxx` (where `Xxx` does not start with a lowercase letter) and take `*testing.T` as a parameter.
- You run tests with the `go test` command.

```go
// main_test.go
package main

import "testing"

func TestAdd(t *testing.T) {
    if add(2, 3) != 5 {
        t.Errorf("add(2, 3) = %d; want 5", add(2, 3))
    }
}
```

## 5. Standard Library

Go has a rich standard library that provides many useful packages. Key packages include:

- `fmt`: For formatted I/O.
- `net/http`: For building HTTP clients and servers.
- `encoding/json`: For encoding and decoding JSON.
- `os`: For operating system-level operations.
- `io`: For I/O primitives.
