[base](../README.md) > [docs](./README.md) > [workflows](./workflows.md) > GitHub Pages Deployment

# GitHub Pages Deployment Workflow

The GitHub Pages deployment workflow is defined in `.github/workflows/pages.yml`. Its purpose is to build and deploy the repository's content as a GitHub Pages website.

## Triggers

This workflow is triggered by:

- A `push` to the `main` branch.
- A manual `workflow_dispatch` event, allowing it to be run from the Actions tab in GitHub.

## Permissions

The workflow is granted the following permissions:

- `contents: read` to read the repository's content.
- `pages: write` to deploy to GitHub Pages.
- `id-token: write` to authenticate with GitHub Pages.

## Concurrency

The workflow uses a concurrency group named `"pages"` to ensure that only one deployment runs at a time. If a new workflow run is triggered while another is in progress, the new run will be queued. However, in-progress runs are not cancelled.

## Jobs

### `build`

This job runs on `ubuntu-latest` and performs the following steps to build the site:

1.  **Checkout**: Checks out the repository's code.
2.  **Setup Pages**: Configures the GitHub Pages environment.
3.  **Build with Jekyll**: Uses the `actions/jekyll-build-pages` action to build the site with Jekyll. The source is the root of the repository (`./`), and the destination for the built site is `./_site`.
4.  **Upload artifact**: Uploads the built site as a GitHub Pages artifact.

### `deploy`

This job also runs on `ubuntu-latest` and depends on the successful completion of the `build` job. It performs the following steps to deploy the site:

1.  **Deploy to GitHub Pages**: Uses the `actions/deploy-pages` action to deploy the artifact from the `build` job to GitHub Pages. The environment is configured for `github-pages`, and the URL of the deployed site is made available as an output.
