[base](../README.md) > [docs](./README.md) > [development](./development.md) > package.json Guide

# `package.json` and `package-lock.json`

You may notice `package.json` and `package-lock.json` files in the root of
this repository.
These files are part of the Node.js ecosystem and are used to manage project
dependencies and scripts.

## What is their Purpose in `base`?

The `attogram/base` template is designed to be language-agnostic.
However, it does use a few Node.js-based tools for development purposes to
ensure code quality and consistency.

- **`package.json`**: This file lists the development dependencies required to
  work on this repository.
  Primarily, this includes `prettier`, a code formatter that automatically
  ensures all configuration files and documentation adhere to a consistent
  style.
  It may also contain simple scripts that can be run with
  `npm run <script_name>`.

- **`package-lock.json`**: This is an auto-generated file that records the
  exact version of every dependency used.
  This guarantees that every developer (and every AI agent) uses the exact
  same version of the tools, preventing inconsistencies and "it works on my
  machine" problems.
  **You should not edit this file manually.**

## Do I Need Node.js?

Strictly speaking, you only need Node.js and `npm` installed if you intend to
run the development tools yourself, such as running
`npx prettier --write .` to format files.

The AI agents that work on this repository are expected to have these tools
available and will use them to keep the codebase consistent.
If you ask an AI agent to perform work, it will use these files to ensure its
changes match the project's standards.

If you are not a developer and are only using this repository to manage
content, you can generally ignore these files.
They are part of the "scaffolding" that keeps the project clean and
maintainable.
