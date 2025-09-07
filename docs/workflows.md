[base](../README.md) > [docs](./README.md) > workflows

# CI/CD Workflows

This repository includes several GitHub Actions workflows to automate various tasks. Each workflow is defined in a `.yml` file in the `.github/workflows` directory.

Below is an overview of the available workflows. For more detailed information about a specific workflow, please refer to its dedicated documentation page.

## Workflow Index

- [**CI Workflow**](./workflows.ci.md) (`ci.yml`) - Ensures code quality by running linting checks on every push and pull request to the `main` branch.
- [**GitHub Pages Deployment**](./workflows.pages.md) (`pages.yml`) - Builds and deploys the repository's content as a GitHub Pages website.
- [**Prettier Workflow**](./workflows.prettier.md) (`prettier.yml`) - Automatically formats the code in the repository using Prettier and commits the changes.
- [**Release on Tag**](./workflows.release-on-tag.md) (`release-on-tag.yml`) - Automates the creation of GitHub Releases when a new version tag is pushed.
- [**Secrets Management**](./workflows.secrets-management.md) - Best practices for managing secrets in GitHub Actions.
- [**Workflow Scheduling**](./workflows.scheduling.md) - Automating recurring tasks with cron.
