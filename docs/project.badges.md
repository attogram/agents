[base](../README.md) > [docs](./README.md) > [project](./project.md) > Repository Badges

# Badges

Badges are a common way to display the status of your project in your
`README.md` file.
They can provide information about your build status, code coverage, version,
license, and more.
They serve as a quick visual indicator of the health and status of your
project.

## Badge Sources

While [Shields.io](https://shields.io/) is very popular because it offers a
huge variety of badges with a consistent style, many services provide their
own free badges directly.
Here are a few examples of common sources:

- **GitHub Actions:** As seen in the examples below, GitHub provides its own
  status badges for workflows.
  You can get the markdown for this directly from the "Actions" tab in your
  repository.

- **CI/CD Services:** Services like [Travis CI](https://travis-ci.org/),
  [CircleCI](https://circleci.com/), and others provide status badges that
  you can embed in your README.

- **Code Coverage Tools:** Services like [Codecov](https://codecov.io/) or
  [Coveralls](https://coveralls.io/) give you badges to show your test
  coverage percentage.

- **Package Registries:** If your project is a package, registries like
  [npm](https://www.npmjs.com/), [PyPI](https://pypi.org/),
  [RubyGems](https://rubygems.org/), etc., offer badges to show the latest
  version, number of downloads, and more.

[Shields.io](https://shields.io/) is a great one-stop-shop that can create
badges for all of the services above and many more, all with a consistent
style.
It can also be used to create completely custom badges.

## Common Badge Categories

Here are some of the most common categories of badges you might see in a
project's `README.md`.

### Build Status

These badges show the status of your continuous integration (CI) builds.
This is one of the most important badges as it tells contributors whether the
project is currently in a working state.

**GitHub Actions**

[![GitHub Actions Workflow Status](https://img.shields.io/github/actions/workflow/status/attogram/base/ci.yml?branch=main)](https://github.com/attogram/base/actions/workflows/ci.yml)

```markdown
[![GitHub Actions Workflow Status](https://img.shields.io/github/actions/workflow/status/attogram/base/ci.yml?branch=main)](https://github.com/attogram/base/actions/workflows/ci.yml)
```

### Releases

These badges show the latest release version of your project.

**GitHub Release**

[![GitHub release (latest by date)](https://img.shields.io/github/v/release/attogram/base)](https://github.com/attogram/base/releases)

```markdown
[![GitHub release (latest by date)](https://img.shields.io/github/v/release/attogram/base)](https://github.com/attogram/base/releases)
```

### Social

These badges show statistics from social coding platforms like GitHub.

**GitHub Stars**

[![GitHub Repo stars](https://img.shields.io/github/stars/attogram/base?style=social)](https://github.com/attogram/base/stargazers)

```markdown
[![GitHub Repo stars](https://img.shields.io/github/stars/attogram/base?style=social)](https://github.com/attogram/base/stargazers)
```

**GitHub Forks**

[![GitHub forks](https://img.shields.io/github/forks/attogram/base?style=social)](https://github.com/attogram/base/network/members)

```markdown
[![GitHub forks](https://img.shields.io/github/forks/attogram/base?style=social)](https://github.com/attogram/base/network/members)
```

### License

It's a good practice to include a badge for your project's license.

**GitHub License**

[![GitHub](https://img.shields.io/github/license/attogram/base)](./LICENSE)

```markdown
[![GitHub](https://img.shields.io/github/license/attogram/base)](./LICENSE)
```

## How many badges is too many?

While badges are useful, having too many can clutter your `README.md` and make
it difficult to read.
A good rule of thumb is to include badges that are most relevant to your
project and its contributors.

Consider these questions when deciding which badges to include:

- **Is it important for contributors to see this information at a glance?**
  (e.g., build status, license)
- **Does this badge provide a link to a useful resource?** (e.g.,
  documentation, releases)
- **Does this badge add value to the project?** (e.g., code coverage,
  version)

If the answer to these questions is "yes," then the badge is probably worth
including.

## Custom Badges

You can also create your own custom badges using Shields.io.
This is useful for linking to things that don't have a pre-made badge.

For example, you could create a badge to link to your project's
documentation:

[![Documentation](https://img.shields.io/badge/documentation-yes-brightgreen.svg)](./docs/README.md)

```markdown
[![Documentation](https://img.shields.io/badge/documentation-yes-brightgreen.svg)](./docs/README.md)
```

You can create your own badges by visiting the
[Shields.io](https://shields.io/) website and using their badge creation tool.
