[base](../README.md) > [docs](./README.md) > [project](./project.md) > Template Repo Guide

# Maintaining `base` as a Template Repository

This document is for maintainers of the `base` repository.
It outlines the best practices and administrative steps required to ensure this
repository functions correctly as a
[GitHub Template](https://docs.github.com/en/repositories/creating-a-repository-on-github/creating-a-repository-from-a-template).

## GitHub Settings

Ensure the following setting is enabled in the repository's main settings page
(`Settings` > `General`):

- [x] **Template repository**

This allows users to generate new repositories from this one.

## Writing Content for the Template

When adding or modifying files, remember that they will be copied verbatim into
new repositories.

- **Use Placeholders:** For project-specific information like copyright notices
  or contact information, use clear placeholders like `[year] [fullname]` or
  `[INSERT CONTACT METHOD]`.
- **Write Instructional Content:** Files like
  [`CONTRIBUTING.md`](../CONTRIBUTING.md) and
  [`CODE_OF_CONDUCT.md`](../CODE_OF_CONDUCT.md) should not be prescriptive.
  Instead, they should guide the end-user on how to create their own versions
  of these files.
- **Relative Links:** Use relative links for all in-repository links (e.g.,
  `[link text](./path/to/file.md)`) to ensure they work correctly in the
  generated repositories.

## Maintainer Checklist

Before tagging a new release of `base`, review the following:

- [ ] All documentation in the [`docs/`](./) directory is up-to-date with the
      latest changes.
- [ ] All workflows in [`.github/workflows/`](../.github/workflows/) are
      tested and functioning.
- [ ] All placeholder files are clear and provide good guidance.
- [ ] The [`AGENTS.md`](../AGENTS.md) file has been updated to reflect any
      changes that would affect AI assistants.
