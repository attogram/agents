[base](../README.md) > [docs](./README.md) > [community](./community.md) > Issue Management Guide

# Issue Management Guide

Effective issue management is key to keeping your project organized and your
community engaged.
This guide covers best practices for using GitHub Issues, labels, and
templates to triage bug reports and feature requests.

## 1. Use Issue Templates

The first step to effective issue management is to get clear, structured
information from contributors.
GitHub's issue templates are perfect for this.

- **What they are:** Pre-populated templates for bug reports and feature
  requests that prompt the user for specific information.
- **Why they're useful:** They ensure you get the information you need to act
  on an issue, such as steps to reproduce a bug or the use case for a new
  feature.
- **How to use them:** This repository includes templates in the
  [`.github/ISSUE_TEMPLATE/`](../.github/ISSUE_TEMPLATE/) directory.
  You can customize them to fit your project's needs.

## 2. Leverage Labels

Labels are a powerful tool for categorizing and prioritizing issues.
A good set of labels makes it easy to see the state of your project at a
glance.

### Recommended Label Categories

- **Issue Type:**
  - `bug`: A problem with the existing code.
  - `feature-request`: A proposal for new functionality.
  - `documentation`: An issue related to the docs.
  - `maintenance`: Chores like refactoring or updating dependencies.

- **Status:**
  - `needs-triage`: A new issue that hasn't been reviewed yet.
  - `confirmed`: A bug report that has been reproduced.
  - `in-progress`: An issue that is actively being worked on.
  - `blocked`: An issue that cannot be worked on due to external factors.

- **Priority:**
  - `critical`: Must be addressed immediately (e.g., a security
    vulnerability).
  - `high`: Important and should be prioritized.
  - `medium`: A standard issue.
  - `low`: A non-urgent issue or nice-to-have feature.

- **Contribution Welcome:**
  - `good-first-issue`: A relatively simple issue that's a great entry point
    for new contributors.
  - `help-wanted`: An issue that you'd like the community to help with.

## 3. The Triage Workflow

Triage is the process of reviewing new issues and preparing them for work.
A typical workflow looks like this:

1.  **Review New Issues:** Regularly check for issues that don't have any
    labels or assignees.

2.  **Ensure Clarity:** If an issue is unclear, ask the author for more
    information.
    If they don't respond after a reasonable amount of time, it's okay to
    close the issue.

3.  **Reproduce Bugs:** For bug reports, try to reproduce the issue based on
    the information provided.
    If you can reproduce it, add a `confirmed` label.
    If not, ask for more details.

4.  **Apply Labels:** Add the appropriate `type`, `status`, and `priority`
    labels to the issue.

5.  **Engage with the Community:**
    - For valid feature requests, discuss the proposal with the community to
      gauge interest and gather ideas.
    - For issues you won't address, explain why and close the issue
      respectfully.
    - For issues that are good for new contributors, add a `good-first-issue`
      label and perhaps a comment with pointers on how to get started.

## 4. Use Milestones and Projects

- **Milestones:** Group issues together for a specific release (e.g.,
  `v1.1.0`).
  This helps you track progress towards your next version.
- **GitHub Projects:** For more complex work, use a project board to visualize
  and manage the workflow of issues and pull requests, similar to a Kanban
  board.

By implementing these practices, you can create a clear, organized, and
efficient issue management process that will benefit both you and your
contributors.
