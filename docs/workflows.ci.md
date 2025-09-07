[base](../README.md) > [docs](./README.md) > [workflows](./workflows.md) > CI Workflow

# CI Workflow

The CI (Continuous Integration) workflow is defined in `.github/workflows/ci.yml`.

## Triggers

This workflow is triggered by the following events:

- `push` to the `main` branch
- `pull_request` to the `main` branch

## Jobs

### `lint`

This job, named "Lint Code Base", runs on the latest version of Ubuntu. It performs the following steps:

1.  **Checkout Code**: Checks out the repository's code.
2.  **Setup Node.js**: Sets up Node.js version 20.
3.  **Install Prettier**: Installs the Prettier code formatter globally.
4.  **Run Prettier**: Runs `prettier --check .` to verify that all files in the repository are formatted correctly according to the Prettier configuration.

The purpose of this workflow is to ensure that all code pushed to the `main` branch or included in a pull request to `main` adheres to the project's coding style, as defined by Prettier. This helps maintain code consistency and quality.
