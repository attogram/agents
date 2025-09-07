[base](../README.md) > docs

# Documentation

[Guides](#guides) - [Development](#development) - [CI/CD Workflows](#cicd-workflows) - [Publishing](#publishing) - [Updating](#updating) - [Project Management](#project-management) - [Community](#community) - [AI](#ai) - [Documentation Best Practices](#documentation-best-practices)

## Guides

- [Software Project Guide](./guides.software-project.md) - Using this repo as a foundation for a software project.

## Development

- [GitHub Codespaces](./development.codespaces.md) - Using Codespaces for cloud-based development.
- [Docker Environment](./development.docker.md) - Using the included Docker setup.
- [`package.json` Guide](./development.package-json.md) - Explanation of the `package.json` files.
- [Using Prettier](./development.prettier.md) - Guide to installing and using Prettier.
- [Prettier Workflow](./development.prettier-workflow.md) - Manually formatting code.

## CI/CD Workflows

- [**CI Workflow**](./workflows.ci.md) (`ci.yml`) - Ensures code quality by running linting checks on every push and pull request to the `main` branch.
- [**GitHub Pages Deployment**](./workflows.pages.md) (`pages.yml`) - Builds and deploys the repository's content as a GitHub Pages website.
- [**Prettier Workflow**](./workflows.prettier.md) (`prettier.yml`) - Automatically formats the code in the repository using Prettier and commits the changes.
- [**Release on Tag**](./workflows.release-on-tag.md) (`release-on-tag.yml`) - Automates the creation of GitHub Releases when a new version tag is pushed.
- [**Secrets Management**](./workflows.secrets-management.md) - Best practices for managing secrets in GitHub Actions.
- [**Workflow Scheduling**](./workflows.scheduling.md) - Automating recurring tasks with cron.

## Publishing

- [Publishing with Markdown](./publishing.markdown.md) - The simplest way to get started with publishing content.
- [Advanced Publishing with HTML](./publishing.html.md) - For those who need more control over their site's layout and appearance.
- [Publishing with Magic Links](./publishing.magic-links.md) - A powerful feature for community-driven sites.
- [GitHub Pages](./publishing.github-pages.md) - More detail on how the underlying GitHub Pages service works.

## Updating

- [Adding `base` to an Existing Repo](./updating.adding-base-to-existing-repo.md) - How to merge `base` into a project that was not created from the template.
- [Syncing When `base` is Updated](./updating.syncing-your-repo-when-base-is-updated.md) - How to get the latest changes from `base` after you have already merged it.

## Project Management

- [Repository Badges](./project.badges.md) - How to use and create repository badges.
- [Launch Checklist](./project.launch-checklist.md) - A reusable checklist for project launches.
- [Licensing Info](./project.licensing.md) - Details on the MIT License.
- [Security Best Practices](./project.security.md) - Basic security practices for maintainers.
- [Standard Files](./project.standard-files.md) - Explanation of standard repo files.
- [Template Repo Guide](./project.template-repo.md) - Best practices for maintaining this template.
- [Versioning Guide](./project.versioning.md) - Professional release management.

## Community

- [Community Building Guide](./community.building.md) - Fostering a healthy and effective community.
- [Using GitHub Discussions](./community.discussions.md) - Leveraging Discussions for community conversations.
- [Issue Management Guide](./community.issue-management.md) - Best practices for triaging issues.

## AI

- [Guiding AI with `AGENTS.md`](./ai.agents-md.md) - Using `AGENTS.md` to provide instructions to AI agents.
- [Prompting AI Agents](./ai.prompting.md) - How to effectively prompt AI agents.

## Documentation Best Practices

- [Documentation Best Practices](./documentation.best-practices.md) - How to write clear and effective documentation.
