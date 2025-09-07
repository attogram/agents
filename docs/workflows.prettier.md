[base](../README.md) > [docs](./README.md) > [workflows](./workflows.md) > Prettier Workflow

# Prettier Workflow

The Prettier workflow, defined in `.github/workflows/prettier.yml`, automates code formatting for the entire repository.

## Triggers

This workflow is triggered on:

- `push` to the `main` branch
- Any `pull_request`

## Jobs

### `format`

This job runs on `ubuntu-latest` and performs the following steps:

1.  **Checkout Code**: Checks out the repository's code. It uses the `GITHUB_TOKEN` to allow the workflow to push changes back to the repository.
2.  **Setup Node.js**: Sets up Node.js version 20 and configures caching for `npm` to speed up dependency installation.
3.  **Install Dependencies**: Installs the project's dependencies, including Prettier, by running `npm install`.
4.  **Run Prettier**: Executes `npx prettier --write .` to format all files in the repository in-place.
5.  **Commit Changes**: Uses the `stefanzweifel/git-auto-commit-action` to check if Prettier made any changes. If there are changes, it commits them back to the current branch with the commit message "style: Format code with Prettier". This action is configured to check all files.

The purpose of this workflow is to ensure that all code in the repository is consistently formatted according to the Prettier rules, without requiring developers to run Prettier manually before committing.
