[base](../README.md) > [docs](./README.md) > [development](./development.md) > Docker Environment

# Docker-based Development Environment

This repository includes a Docker-based development environment to ensure a
consistent and reproducible setup for all contributors.

## Components

The environment is defined by several files:

- **[`docker/Dockerfile`](../docker/Dockerfile)**: This is the blueprint for
  our development image.
  It starts from a standard Ubuntu 22.04 base, then installs NGINX and a set
  of common, language-agnostic development tools (`git`, `curl`,
  `build-essential`, etc.).
- **[`docker/nginx.conf`](../docker/nginx.conf)**: This is a standard
  configuration file for the NGINX web server.
  It's set up to serve the content of the `docker/html` directory.
- **[`docker/html/index.html`](../docker/html/index.html)**: This simple file
  contains the word `pong` and is served by NGINX.
  It provides a simple way to check if the environment is running correctly (a
  "health check").
- **[`docker-compose.yml`](../docker-compose.yml)**: This file makes it easy
  to build and run the development environment.
  It defines a single service named `dev` and maps port 80 inside the
  container to port 8080 on your local machine.
- **[`.dockerignore`](../.dockerignore)**: This file tells Docker which files
  and directories to exclude from the build context, which helps to speed up
  the image build process.

## Getting Started

To use the development environment, you must have
[Docker](https://www.docker.com/get-started) and
[Docker Compose](https://docs.docker.com/compose/install/) installed on your
system.

1.  **Build and Run the Container:**
    Open a terminal in the root of the repository and run the following
    command:

    ```bash
    docker-compose up -d
    ```

    This will build the Docker image (if it's the first time) and start the
    container in the background.

2.  **Verify It's Running:**
    Open your web browser and navigate to `http://localhost:8080`.
    You should see the word `pong`.

3.  **Access the Environment:**
    To open a shell inside the running container, use the following command:

    ```bash
    docker-compose exec dev /bin/bash
    ```

    You will now be inside the Ubuntu environment, where you can install any
    language-specific tools (like Python, Node.js, etc.) and run your code.

4.  **Stopping the Environment:**
    To stop the container, run:
    ```bash
    docker-compose down
    ```

## Extending the Environment

You can easily extend this environment by modifying the
[`docker/Dockerfile`](../docker/Dockerfile).
For example, to install Python, you could add the following line:

```Dockerfile
RUN apt-get update && apt-get install -y python3 python3-pip
```
