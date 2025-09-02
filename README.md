# Agents

> A collection of `AGENTS.md` templates for guiding AI assistants.

Use these `AGENTS.md` files to provide clear instructions for AI coding assistants, ensuring they align with your project's standards and technologies.

---

## The `AGENTS.md` Philosophy

An `AGENTS.md` file serves as a set of instructions for an external AI helper, like a coding assistant in your IDE or a chatbot. Think of it as a `CONTRIBUTING.md` for AI collaborators. It sets the rules of engagement, defines the project's boundaries, and clarifies how the AI can be most helpful.

The goal is to leverage AI assistance effectively for development tasks like debugging, refactoring, documentation, and testing.

## How to Use

1.  Choose the `AGENTS.md` template that best fits your project's technology stack.
2.  Copy the file into the root of your repository and name it `AGENTS.md`.
3.  Customize it with specific details about your project (e.g., build commands, test scripts, coding standards).

## Included Templates

This repository provides a set of templates to start from:

- [`AGENTS.md`](./AGENTS.md): A generic template suitable for any project. It provides a good starting point for customization.
- [`AGENTS.php.md`](./AGENTS.php.md): A template for general PHP projects, with guidelines for PHPUnit and PSR-12 standards.
- [`AGENTS.php.laravel.md`](./AGENTS.php.laravel.md): A template for Laravel projects, including instructions for Pest and Artisan commands.
- [`AGENTS.bash.bats.md`](./AGENTS.bash.bats.md): A template for Bash projects that use BATS for testing.

---

## Example Agent Profile

In addition to templates, this repository also contains an example of a "filled-out" agent profile for an AI assistant named Jules. This file, `AGENTS.jules.md`, documents the specific tools and capabilities of that agent. It can serve as a reference for how an `AGENTS.md` file can be used to document an AI's development environment.

- [`AGENTS.jules.md`](./AGENTS.jules.md): An example profile for the AI assistant, Jules.
