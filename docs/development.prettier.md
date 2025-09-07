[base](../README.md) > [docs](./README.md) > [development](./development.md) > Using Prettier

# Prettier for Code Formatting

[Prettier](https://prettier.io/) is an opinionated code formatter that enforces a consistent code style across the entire project. This repository is configured to use Prettier in two ways: automatically via a GitHub workflow and manually for local development.

## Automated Formatting with GitHub Actions

This repository includes a [GitHub Actions workflow](./workflows.prettier.md) that automatically formats all code.

- **How it works**: The workflow runs on every push to the `main` branch and on every pull request. It runs `prettier --write .` to format all files and commits any changes with the message "style: Format code with Prettier".
- **What you need to do**: Nothing! The workflow handles everything automatically. If you push code that isn't formatted, the workflow will create a new commit with the required formatting changes.

This ensures that all code merged into the `main` branch is consistently formatted.

## Manual Formatting

While the automated workflow handles formatting on the server, it's a good practice to run Prettier locally as you work.

### Installation

This repository includes Prettier as a development dependency in `package.json`. To install it, run:

```bash
npm install
```

The repository also includes a [`.prettierrc`](../.prettierrc) configuration file, so you don't need to create one.

### Usage

You can run Prettier from the command line to format your files.

- **Format all files**:
  ```bash
  npx prettier . --write
  ```
- **Check for formatting issues without changing files**:
  ```bash
  npx prettier . --check
  ```
  The [CI workflow](./workflows.ci.md) uses this command to validate formatting on pull requests.

For more detailed information on using Prettier, refer to the [official Prettier documentation](https://prettier.io/docs/en/).
