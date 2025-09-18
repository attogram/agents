# Working with C++

This document provides guidelines and best practices for AI agents working on C++ projects. The focus is on **Modern C++ (C++11 and newer)**, which introduced features that make the language safer, more expressive, and easier to use.

## 1. Development Environment

A C++ project requires a compiler, a build system, and often a package manager.

### Compilers

- **GCC (GNU Compiler Collection)**: The `g++` compiler is the standard on most Linux systems.
- **Clang**: A modern compiler from the LLVM project, known for its excellent error messages.
- **MSVC**: The Microsoft Visual C++ compiler, standard on Windows.

### Build Systems

**CMake** is the de-facto standard build system for modern C++ projects. It uses a script named `CMakeLists.txt` to define the build process.

- **`CMakeLists.txt`**: This file contains a set of directives and commands that describe the project's source files and dependencies.

- **Basic `CMakeLists.txt` Example**:

  ```cmake
  # Specify the minimum version of CMake required.
  cmake_minimum_required(VERSION 3.10)

  # Set the project name and language.
  project(MyProject CXX)

  # Specify the C++ standard.
  set(CMAKE_CXX_STANDARD 17)
  set(CMAKE_CXX_STANDARD_REQUIRED ON)

  # Add an executable target.
  add_executable(my_app main.cpp)
  ```

- **Building with CMake**:
  ```bash
  mkdir build
  cd build
  cmake ..
  make
  ```

### Package Management

Managing dependencies in C++ can be complex. Package managers help automate this process.

- **vcpkg (Microsoft)**: A cross-platform package manager.
- **Conan**: Another popular, cross-platform package manager.

## 2. Key Language Features (Modern C++)

### RAII and Smart Pointers

**RAII (Resource Acquisition Is Initialization)** is a core C++ principle. It means that you tie the life cycle of a resource (like memory, a file handle, or a network socket) to the lifetime of an object. The resource is acquired in the object's constructor and released in its destructor.

**Smart Pointers** are the primary way to implement RAII for memory management. They automatically handle memory deallocation, preventing memory leaks.

- `std::unique_ptr`: A smart pointer that owns and manages another object through a pointer and disposes of that object when the `unique_ptr` goes out of scope. There can only be one `unique_ptr` to an object.
- `std::shared_ptr`: A smart pointer that retains shared ownership of an object through a pointer. Several `shared_ptr` objects may own the same object. The object is destroyed when the last remaining `shared_ptr` owning it is destroyed.
- `std::weak_ptr`: A smart pointer that holds a non-owning ("weak") reference to an object that is managed by a `shared_ptr`. It is used to break circular references.

**Always prefer smart pointers over raw pointers (`new` and `delete`) for managing dynamic memory.**

### The Standard Template Library (STL)

The STL is a set of C++ template classes to provide common data structures and functions.

- **Containers**:
  - `std::vector`: A dynamic array.
  - `std::string`: A string class.
  - `std::map`: A key-value map (implemented as a red-black tree).
  - `std::unordered_map`: A key-value map (implemented as a hash table).
- **Algorithms**: The `<algorithm>` header provides a rich set of functions for operating on ranges of elements (e.g., `std::sort`, `std::find`, `std::for_each`).

### Lambdas

Lambdas are a concise way to create anonymous functions.

```cpp
#include <vector>
#include <algorithm>
#include <iostream>

int main() {
    std::vector<int> v = {1, 2, 3, 4, 5};
    std::for_each(v.begin(), v.end(), [](int n) {
        std::cout << n << std::endl;
    });
    return 0;
}
```

## 3. Testing

- **Google Test (`gtest`)**: A popular and powerful C++ testing framework. It provides a rich set of assertions and features for writing tests.
- **Catch2**: Another popular, modern, and easy-to-use testing framework.

A typical test with Google Test looks like this:

```cpp
#include "gtest/gtest.h"

int add(int a, int b) {
    return a + b;
}

TEST(AddTest, PositiveNumbers) {
    EXPECT_EQ(add(2, 3), 5);
}
```
