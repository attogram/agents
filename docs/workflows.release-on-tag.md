[base](../README.md) > [docs](./README.md) > [workflows](./workflows.md) > Release on Tag

# Release on Tag Workflow

The "Create Release" workflow, defined in `.github/workflows/release-on-tag.yml`, automates the process of creating a new GitHub release whenever a new tag is pushed to the repository.

## Triggers

This workflow is triggered when a `push` event occurs with a tag that matches the pattern `v*.*.*` (e.g., `v1.0.0`, `v2.3.4`).

## Jobs

### `build`

This job runs on `ubuntu-latest` and has `contents: write` permissions to allow it to create a release. It performs the following steps:

1.  **Checkout code**: Checks out the repository's code. `fetch-depth: 0` is used to fetch all history for all branches and tags, which is necessary for generating the changelog.

2.  **Generate release notes**: This step generates the body of the release notes. It does this by:
    - Identifying the previous tag to determine the range of commits to include in the changelog.
    - Generating a changelog from the Git history between the previous tag and the current `HEAD`. The changelog format is a list of commit messages, each with a link to the corresponding commit.
    - Reading the release body template from `.github/RELEASE_BODY.md` and substituting the `${TAG}` placeholder with the current tag name.
    - Combining the user-provided body, the generated changelog, and a link to the full diff on GitHub into a single `FINAL_BODY` output.

3.  **Get Release Title**: This step reads the release title template from `.github/RELEASE_TITLE.txt`, replaces the `${TAG}` placeholder with the current tag name, and sets the result as an output named `title`.

4.  **Create Release**: This final step uses the `softprops/action-gh-release` action to create the GitHub release. It uses the title and body generated in the previous steps, and sets the `tag_name` to the tag that triggered the workflow. The release is created as a full release (not a draft or pre-release).

This workflow streamlines the release process by automating the creation of well-formatted, consistent GitHub releases based on Git tags.
