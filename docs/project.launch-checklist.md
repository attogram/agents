[base](../README.md) > [docs](./README.md) > [project](./project.md) > Launch Checklist

# Project Launch Checklist

Launching a new open-source project can be a daunting task.
This checklist is designed to help you ensure a smooth and successful launch.

## Pre-Launch

This is the phase where you prepare your project for its public debut.

### Initial Repository Setup

These are the very first steps to take after creating a new repository from the `base` template.

- [ ] **Choose a Repository Name:**
  - **Max Characters:** 100
  - **Advice:** Pick a name that is short, memorable, and descriptive of your project. Avoid using spaces; use hyphens (`-`) or underscores (`_`) instead.

- [ ] **Write a Description:**
  - **Max Characters:** 350
  - **Advice:** This is your project's "elevator pitch." Briefly explain what your project does and who it's for. This description is shown in search results and on the repository page.

- [ ] **Set Up GitHub Pages Publishing:**
  1. Go to your repository's **Settings** tab.
  2. In the left sidebar, click on **Pages**.
  3. Under "Build and deployment," for the **Source**, select **GitHub Actions**. This repository is pre-configured with a workflow to build and deploy your site.

- [ ] **Publish Test:**
  1. Make a small, visible edit to the `README.md` file (e.g., add a sentence).
  2. Commit and push the change to the `main` branch.
  3. Go to the **Actions** tab of your repository and wait for the `pages` workflow to complete successfully.
  4. Visit your new GitHub Pages URL (e.g., `https://<your-username>.github.io/<your-repo-name>/`) to confirm that your change is live.

- [ ] **Tag an Initial Release (`v0.0.1`):**
  - This step confirms that your release workflow is functioning correctly.
  - Run the following commands in your local terminal:
    ```bash
    git tag -a v0.0.1 -m "Initial setup and project scaffolding"
    git push origin main --tags
    ```
  - Go to the **Releases** page on your repository to confirm that a new `v0.0.1` release has been created automatically.

### Code and Repository

- [ ] Finalize initial feature set for `v1.0.0`.
- [ ] Write comprehensive tests and ensure they are all passing.
- [ ] Set up CI/CD workflows for testing and linting.
- [ ] Polish the codebase: remove commented-out code, fix typos, and ensure
      consistent styling.
- [ ] Run a security audit (e.g., check dependencies for known
      vulnerabilities).

### Documentation

- [ ] Write a clear and compelling `README.md`.
- [ ] Create a `CONTRIBUTING.md` file with guidelines for contributors.
- [ ] Add a `LICENSE` file (e.g., MIT, Apache 2.0).
- [ ] Write user guides and API reference documentation.
- [ ] Add a `CODE_OF_CONDUCT.md` to set community standards.

### Community & Marketing

- [ ] Prepare a blog post or announcement for the launch.
- [ ] Identify communities (e.g., Reddit, Hacker News, specific forums) where
      you will share your project.
- [ ] Create a project website or landing page (GitHub Pages is a great
      option).
- [ ] Set up social media accounts if desired.

## Launch Day

The day you make your project public.

- [ ] **Publish your code:** Make your GitHub repository public.
- [ ] **Push the `v1.0.0` tag:** This will trigger your automated release
      workflow.
  ```bash
  git tag -a v1.0.0 -m "Initial public release"
  git push origin main --tags
  ```
- [ ] **Monitor for feedback:** Keep a close eye on GitHub issues, social
      media, and other channels for questions and bug reports.
- [ ] **Be responsive:** Engage with early adopters, answer questions, and
      thank them for their interest.

## Post-Launch

The work doesn't stop after launch day.
Now it's about building momentum.

### Short-Term (First Week)

- [ ] Triage and fix critical bugs reported by early users.
- [ ] Publish a `v1.0.1` patch release if necessary.
- [ ] Thank the community for the feedback and support.
- [ ] Share any positive press or comments.

### Long-Term (First Month and Beyond)

- [ ] Continue to be responsive to issues and pull requests.
- [ ] Start working on the features planned for `v1.1.0`.
- [ ] Nurture your community by empowering contributors (see the
      [Community Building Guide](./community-building-guide.md)).
- [ ] Set up a regular release cadence.
- [ ] Periodically review and update your documentation.

This checklist is a starting point.
Feel free to adapt it to the specific needs of your project.
Good luck with your launch!
