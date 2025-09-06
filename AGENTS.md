AGENTS.md v0.0.1

# AI Assistant Instructions

This document provides instructions for AI assistants working on this project. Related documents:
- [HUMANS.md](./HUMANS.md)
- [README.md](./README.md)
- [CONTRIBUTING.md](./CONTRIBUTING.md)

## Agent Personas

- [Claude](agents/AGENTS.claude.md)
- [Claude Code](agents/AGENTS.claude.code.md)
- [Jules](agents/AGENTS.jules.md)

## Core Objective

Your primary goal is to assist with developing, debugging, and testing new features, while adhering to the project's standards for code quality and testing.

## Project Overview

- **Project Name:** Acme Corp Web App
- **Description:** A web application for managing customer data.
- **Tech Stack:** JavaScript, React, Node.js, Express, PostgreSQL

## Development Workflow

1.  **Dependencies:** This project uses `npm` for dependency management. Install dependencies with `npm install`.
2.  **Running the App:** To run the application locally, use the command `npm run dev`.
3.  **Branching:** Create a new branch for each task. Use the format `feature/short-description`.

## Testing

- **Test Suite:** The test suite is run with the command `npm test`.
- **Testing Policy:** For new features, you must write corresponding tests. For bug fixes, you must first write a failing test that reproduces the bug. All tests must pass before submitting work.

## Coding Standards

- **Style Guide:** This project uses **Prettier** for code formatting. Ensure it is applied before committing.
- **Linter:** We use **ESLint** for identifying and fixing problems in the code. Run the linter with `npm run lint` and fix any reported issues.
- **Key Conventions:**
  - All API responses must be in the JSend format.
  - All functions must have JSDoc-style comments.

## Additional Context

Use this section to add any other important information, links to internal wikis, or context the AI might need to be successful.
