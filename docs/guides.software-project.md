[base](../README.md) > [docs](./README.md) > [guides](./guides.md) > Software Project Guide

# Use Case: A Starting Point for Your Software Project

This repository is designed to be a robust foundation for a wide variety of
software projects.
It provides a standardized, best-practice setup that lets you focus on
writing code, not on boilerplate and configuration.

This guide will walk you through how to adapt this template for different
kinds of software projects, with examples for common languages and platforms.

## Core Philosophy: A "Batteries-Included" Template

The `base` repository is built on the idea that a good starting point can
save hours or even days of setup time.
It provides:

- **A Consistent Development Environment:** Using Docker and GitHub Codespaces,
  everyone on your team has the same setup, eliminating "it works on my
  machine" problems.
- **Automated Workflows:** GitHub Actions are pre-configured for common tasks
  like linting, testing, and continuous integration.
- **Standardized Tooling:** Pre-configured tools like Prettier for code
  formatting ensure consistency across the codebase.
- **Clear Documentation:** A `docs` directory and a GitHub Pages site are
  ready for you to document your project.

## Part 1: Structuring Your Project

While this template provides a solid base, you'll need to add your own
application code.
Here are some recommended structures for different project types.

### General Recommendations

- **Source Code:** Keep your main application code in a dedicated directory.
  Common choices are `src/`, `app/`, or a directory named after your project.
- **Tests:** Keep your tests separate from your application code, but in a way
  that mirrors the source structure.
  A top-level `tests/` or `spec/` directory is a common pattern.
- **Scripts:** Place helper scripts, build scripts, or deployment scripts in a
  `scripts/` directory.
- **Configuration:** While this template provides global configuration
  (`.editorconfig`, `.gitignore`), your application will have its own
  configuration.
  Store these in a `config/` directory or at the root of the project,
  depending on the framework.

---

## Part 2: Language- and Platform-Specific Examples

Here's how you can adapt this template for some popular platforms.

### Example: A Node.js Application

Node.js is a popular choice for building web servers, APIs, and command-line
tools.

**1. Project Structure:**

```
.
├── src/
│   ├── index.js      # Main application entry point
│   ├── app.js        # Express app setup
│   ├── routes/
│   │   └── api.js    # API route definitions
│   └── lib/
│       └── utils.js  # Utility functions
├── tests/
│   ├── api.spec.js   # Tests for the API
│   └── utils.spec.js # Unit tests for utility functions
├── package.json      # Project dependencies and scripts
└── ... (rest of the template files)
```

**2. Setting up Dependencies:**

You'll use `npm` or `yarn` to manage your dependencies.

```bash
# Install a web framework like Express
npm install express

# Install development dependencies like a testing framework
npm install --save-dev jest supertest
```

**3. Configuring `package.json`:**

Your `package.json` is the heart of your Node.js project.
You'll add scripts for common tasks.

```json
"scripts": {
  "start": "node src/index.js",
  "dev": "nodemon src/index.js",
  "test": "jest",
  "lint": "eslint src/**/*.js"
}
```

**4. Docker Configuration (`docker-compose.yml`):**

To run your Node.js app in the development environment, you can add a service
to the `docker-compose.yml` file.

```yaml
services:
  app:
    build: .
    ports:
      - "3000:3000"
    volumes:
      - .:/usr/src/app
    command: npm run dev
```

### Example: A PHP/Laravel Project

Laravel is a powerful PHP framework for building web applications.

**1. Project Structure:**

Laravel has its own prescribed directory structure, which you can create
within this template.

```
.
├── app/              # Core application code (models, controllers)
├── bootstrap/
├── config/
├── database/
├── public/           # Web server entry point (index.php)
├── resources/
├── routes/
├── storage/
├── tests/
├── vendor/           # Composer dependencies
├── composer.json
└── ... (rest of the template files)
```

**2. Setting up with Composer:**

You'd typically use Composer to install Laravel and its dependencies.

```bash
# Install Composer dependencies
composer install

# Generate an application key
php artisan key:generate
```

**3. Docker Configuration (`docker-compose.yml`):**

A Laravel setup often requires multiple services (PHP, a web server like
Nginx, a database like MySQL).

```yaml
services:
  app:
    build:
      context: .
      dockerfile: Dockerfile # You'll need a custom Dockerfile for PHP
    volumes:
      - .:/var/www/html
  nginx:
    image: nginx:stable-alpine
    ports:
      - "8080:80"
    volumes:
      - .:/var/www/html
      - ./docker/nginx.conf:/etc/nginx/conf.d/default.conf # Custom Nginx config
  db:
    image: mysql:8.0
    environment:
      MYSQL_DATABASE: my_app
      MYSQL_ROOT_PASSWORD: root_password
```

### Example: A Go Application

Go is excellent for building high-performance, compiled applications.

**1. Project Structure:**

A common Go project structure looks like this:

```
.
├── cmd/
│   └── myapp/
│       └── main.go   # Main application entry point
├── pkg/
│   └── mylib/
│       └── mylib.go  # Reusable library code
├── go.mod            # Go module definition
├── go.sum
└── ... (rest of the template files)
```

**2. Setting up with Go Modules:**

You'll use Go modules to manage dependencies.

```bash
# Initialize a new module
go mod init github.com/your-username/my-project

# Add a dependency
go get -u github.com/gorilla/mux
```

**3. Building and Running:**

You can build and run your Go application directly.

```bash
# Build the binary
go build -o myapp ./cmd/myapp

# Run the application
./myapp
```

**4. Docker Configuration (`Dockerfile`):**

Go applications are often deployed as small, static binaries in a minimal
Docker image.

```dockerfile
# build stage
FROM golang:1.19-alpine AS builder
WORKDIR /app
COPY . .
RUN go build -o /main ./cmd/myapp

# final stage
FROM alpine:latest
WORKDIR /root/
COPY --from=builder /main .
CMD ["./main"]
```

### Example: A Collection of Bash Scripts

You can use this repository to manage a collection of related shell scripts.

**1. Project Structure:**

```
.
├── scripts/
│   ├── main.sh
│   ├── utils.sh
│   └── install.sh
├── tests/
│   ├── test_main.sh
│   └── test_utils.sh
├── lib/              # Optional: for shared functions to be sourced
│   └── helpers.sh
└── ... (rest of the template files)
```

**2. Making Scripts Executable:**

Ensure your scripts have the correct permissions.

```bash
chmod +x scripts/*.sh
```

**3. Testing Bash Scripts:**

You can use a testing framework like `shellcheck` for static analysis and
`bats-core` for unit testing.

**`package.json` for Tooling:**

Even for a Bash project, you can use `package.json` to manage your testing
tools.

```json
"scripts": {
  "lint": "shellcheck scripts/*.sh",
  "test": "bats tests"
}
```

```bash
# Install development dependencies
npm install --save-dev shellcheck bats-core
```

### Example: A Plain JavaScript/Frontend Project

For a project without a heavy framework, you can structure it for serving
static HTML, CSS, and JS files.

**1. Project Structure:**

```
.
├── dist/             # Build output directory
├── src/
│   ├── js/
│   │   └── main.js
│   ├── css/
│   │   └── style.css
│   └── index.html
├── package.json
└── ... (rest of the template files)
```

**2. Development Tooling (`package.json`):**

Use `npm` scripts for development tasks like running a local server and
building your assets.

```json
"scripts": {
  "start": "live-server src/",
  "build": "cp -r src/* dist/"
}
```

```bash
# Install a simple development server
npm install --save-dev live-server
```

**3. GitHub Pages Deployment:**

This setup is perfect for deploying to GitHub Pages.
You can configure a GitHub Action to run your `npm run build` command and
deploy the contents of the `dist/` folder.

See the **[Use Case: A Publishing Platform](./use-case-publishing.md)** guide
for more details on this approach.

---

## Part 3: Adapting the CI/CD Workflows

The included GitHub Actions in `.github/workflows/` provide a starting point.
You'll likely want to customize them for your project.

### Customizing the `ci.yml` Workflow

The main `ci.yml` workflow is a good place to add steps for:

- **Installing Dependencies:** Add a step to run `npm install`,
  `composer install`, or `go get`.
- **Running Tests:** Add a step to execute your test suite (`npm test`,
  `php artisan test`, `go test`).
- **Building Your Application:** If your project needs a build step, add it
  here.
- **Linting:** The workflow already includes `prettier`.
  You can add other linters like `eslint` or `shellcheck`.

**Example: `ci.yml` step for a Node.js project**

```yaml
- name: Install Dependencies
  run: npm install

- name: Run Tests
  run: npm test
```

## Conclusion

This `base` repository is a powerful and flexible starting point.
By understanding its core components and how to adapt them, you can bootstrap
your next software project quickly and efficiently, ensuring you start with a
solid, maintainable, and well-structured foundation.
