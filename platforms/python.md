# Working with Python

This document provides guidelines and best practices for AI agents working on Python projects. Python is a versatile, high-level language known for its readability and extensive standard library.

## 1. Development Environment

A well-defined and isolated development environment is crucial for any Python project.

### Virtual Environments

Always use a virtual environment to manage project-specific dependencies and isolate them from the global Python installation. The standard tool for this is `venv`.

- **Creating a virtual environment**:

  ```bash
  python -m venv .venv
  ```

  This creates a virtual environment in a `.venv` directory.

- **Activating the environment**:
  - On macOS/Linux: `source .venv/bin/activate`
  - On Windows: `.venv\Scripts\activate`

### Package Management

Dependencies are managed using `pip` and a `requirements.txt` file.

- **Installing packages**:
  ```bash
  pip install <package-name>
  ```
- **Freezing dependencies**: To create a `requirements.txt` file that lists all project dependencies and their exact versions:
  ```bash
  pip freeze > requirements.txt
  ```
- **Installing from requirements**: To install all dependencies for a project:
  ```bash
  pip install -r requirements.txt
  ```

### Modern Tooling (Poetry)

For more advanced dependency and project management, consider using [Poetry](https://python-poetry.org/). It combines virtual environment management, dependency resolution, and packaging into a single tool, using a `pyproject.toml` file.

## 2. Code Quality

Maintaining high code quality is essential for collaboration and maintainability.

- **Code Formatting**: Use `black` to automatically format your code. It is an opinionated formatter that ensures a consistent style with minimal configuration.
  ```bash
  pip install black
  black .
  ```
- **Linting**: Use `flake8` to check for style guide (PEP 8) violations, programming errors, and code complexity.
  ```bash
  pip install flake8
  flake8 .
  ```
- **Pre-commit Hooks**: Use the `pre-commit` framework to run these tools automatically before each commit.

## 3. Key Language Features

Modern Python has many powerful features that you should use.

- **Data Structures**:
  - **Lists**: Ordered, mutable collections. `[1, 2, 3]`
  - **Tuples**: Ordered, immutable collections. `(1, 2, 3)`
  - **Dictionaries**: Unordered (in older Python versions), mutable key-value stores. `{'key': 'value'}`
  - **Sets**: Unordered, mutable collections of unique elements. `{1, 2, 3}`

- **F-strings (Formatted String Literals)**: The preferred way to format strings. They are readable and fast.

  ```python
  name = "Jules"
  greeting = f"Hello, {name}!"
  ```

- **List Comprehensions**: A concise and readable way to create lists.

  ```python
  squares = [x**2 for x in range(10)]
  ```

- **Generators**: A simple way to create iterators using the `yield` keyword. They are memory-efficient for large data sets.

  ```python
  def count_up_to(max):
      count = 1
      while count <= max:
          yield count
          count += 1
  ```

- **Decorators**: A way to add functionality to an existing function without modifying its structure.

  ```python
  def my_decorator(func):
      def wrapper():
          print("Something is happening before the function is called.")
          func()
          print("Something is happening after the function is called.")
      return wrapper

  @my_decorator
  def say_whee():
      print("Whee!")
  ```

## 4. Testing

- **`pytest`**: The de-facto standard for testing in Python. It has a simple syntax (using plain `assert` statements), a powerful fixture system, and a rich plugin ecosystem.
- **Running Tests**:
  ```bash
  pip install pytest
  pytest
  ```
- **Example Test**:

  ```python
  # test_example.py
  def add(a, b):
      return a + b

  def test_add():
      assert add(2, 3) == 5
  ```

## 5. The Standard Library

Python has an extensive "batteries-included" standard library. Before reaching for a third-party package, check if the functionality you need is available in the standard library. Some key modules include:

- `os` and `pathlib`: For interacting with the operating system and file paths.
- `sys`: For system-specific parameters and functions.
- `json`: For working with JSON data.
- `datetime`: For working with dates and times.
- `collections`: Provides specialized container datatypes.
