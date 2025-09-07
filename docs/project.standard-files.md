[base](../README.md) > [docs](./README.md) > [project](./project.md) > Standard Files

# Standard Repository Files

This document explains the purpose of the standard, language-agnostic
configuration files included in this repository.

## [`.gitignore`](../.gitignore)

This file tells the `git` version control system which files and directories
to ignore.
The one included in this repository is pre-populated with common ignores for
operating system files (like `.DS_Store` on macOS) and IDE configuration
folders (like `.vscode`).

[Learn more about `.gitignore`](https://git-scm.com/docs/gitignore).

## [`.editorconfig`](../.editorconfig)

This file helps maintain consistent coding styles for multiple developers
working on the same project across various editors and IDEs.
The included file sets basic standards like using spaces for indentation and
trimming trailing whitespace.

[Learn more about EditorConfig](https://editorconfig.org/).

## [`.gitattributes`](../.gitattributes)

This file is used to define attributes per path.
The included file has a single, important rule: `* text=auto eol=lf`.
This enforces consistent line endings (LF) for all text files, which prevents
common issues when developers use different operating systems.

[Learn more about `.gitattributes`](https://git-scm.com/docs/gitattributes).

## [`.prettierrc`](../.prettierrc)

This file configures the [Prettier](https://prettier.io/) code formatter.
Prettier is used in the [`ci.yml`](../.github/workflows/ci.yml) workflow to
ensure that all Markdown and YAML files in the repository have a consistent
style.

[Learn more about Prettier configuration](https://prettier.io/docs/en/configuration.html).
