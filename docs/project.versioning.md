[base](../README.md) > [docs](./README.md) > [project](./project.md) > Versioning Guide

# Versioning and Release Management

A well-defined versioning and release strategy is crucial for any professional
software project.
It provides clarity for consumers of your software and helps maintainers keep
track of changes.
This guide outlines best practices using Semantic Versioning (SemVer) and
GitHub's automated release features.

## Semantic Versioning (SemVer)

Semantic Versioning is a widely adopted versioning scheme that gives meaning
to version numbers.
A version number is composed of three parts: `MAJOR.MINOR.PATCH`.

- **MAJOR** version: Incremented for incompatible API changes.
- **MINOR** version: Incremented for adding functionality in a
  backward-compatible manner.
- **PATCH** version: Incremented for backward-compatible bug fixes.

For example, `v1.2.3` means:

- `1`: Major version 1
- `2`: Minor version 2
- `3`: Patch version 3

Adhering to SemVer helps users understand the impact of upgrading and allows
them to specify dependency versions safely.

### Pre-releases

For versions that are not yet stable, you can use pre-release tags, such as
`1.0.0-alpha.1`, `1.0.0-beta.2`, or `1.0.0-rc.1`.
These are useful for testing and getting feedback before a final release.

## Automated Releases with GitHub

This repository is configured with a GitHub Actions workflow that automates
the process of creating a GitHub Release when you push a new tag.

### How it Works

1.  **Tag a Commit:** When your `main` branch is ready for a release, you
    create a git tag pointing to the commit you want to release.
    The tag name **must** follow Semantic Versioning (e.g., `v1.0.0`,
    `v2.3.1`).

    ```bash
    git tag -a v1.0.0 -m "Initial release"
    git push origin v1.0.0
    ```

2.  **Workflow Trigger:** Pushing the tag to the repository triggers the
    [`.github/release-on-tag.yml`](../.github/workflows/release-on-tag.yml)
    workflow.

3.  **Automated Release Notes:** The workflow automatically generates release
    notes based on the titles of the pull requests merged since the last
    release.
    It categorizes them into sections like "Features," "Bug Fixes," and
    "Maintenance."

4.  **Create Release:** The workflow creates a new GitHub Release with the
    tag, the generated release notes, and any build artifacts you've
    configured.

### Customizing Release Notes

You can customize the title and body of the release notes by editing the
following files:

- [`.github/RELEASE_TITLE.txt`](../.github/RELEASE_TITLE.txt): A one-line
  title for your release.
- [`.github/RELEASE_BODY.md`](../.github/RELEASE_BODY.md): A markdown file
  where you can add introductory text or other custom content to the release
  notes.

By combining Semantic Versioning with automated release workflows, you can
maintain a professional, consistent, and low-friction release process for your
project.
