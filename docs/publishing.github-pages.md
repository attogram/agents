[base](../README.md) > [docs](./README.md) > [publishing](./publishing.md) > GitHub Pages

# GitHub Pages Site

This repository is configured to use [GitHub Pages](https://pages.github.com/)
to host a simple, clean website for the project.

## Initial Setup

Before the workflow can deploy your site, you must configure your repository
to use GitHub Actions for GitHub Pages.
This is a one-time setup step that connects your repository's Pages settings
to the `pages.yml` workflow included in this template.

1.  **Navigate to Repository Settings:** Go to the main page of your
    repository and click on the **Settings** tab.
2.  **Select Pages:** In the left-hand sidebar, click on **Pages**.
3.  **Set the Deployment Source:** Under the "Build and deployment" section,
    you will see a **Source** option.
    Select **"GitHub Actions"** from the dropdown menu.

After you select "GitHub Actions", the UI may present you with suggestions
for common workflows (e.g., "GitHub Pages Jekyll", "Static HTML").
**You can ignore these suggestions.**
This repository already contains a custom, pre-configured workflow
([`.github/workflows/pages.yml`](../.github/workflows/pages.yml)) that will
be used automatically.

> **Note:** If you do not perform this setup step, the
> [`pages.yml`](../.github/workflows/pages.yml) workflow will fail with a
> "Get Pages site failed" or "HttpError: Not Found" error.

## How It Works

The site is built and deployed by the
[`.github/workflows/pages.yml`](../.github/workflows/pages.yml) workflow.
Here's a summary of the process:

1.  **Trigger:** The workflow runs automatically on every push to the `main`
    branch.
2.  **Jekyll Build:** It uses the standard `jekyll-build-pages` GitHub Action
    to build a static website.
3.  **Homepage:** It is configured to use the root [`README.md`](../README.md)
    file as the content for the homepage (`index.html`) of the site.
4.  **Styling:** The [`_config.yml`](../_config.yml) file in the root of the
    repository specifies the `jekyll-theme-primer` theme, which gives the
    site the standard GitHub look and feel.
5.  **Deployment:** The built static site is then deployed to GitHub Pages.

## Accessing the Site

After the first push to `main`, the site will be available at a URL like:

`https://<your-username>.github.io/<your-repository-name>/`

You can also find the URL in the "Pages" section of your repository's
settings.
