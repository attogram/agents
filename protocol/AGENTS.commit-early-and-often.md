# Protocol: Commit Early and Often

This document is a starter prompt for AI assistants.

## Bootstrap Protocol

**Your first action in any new session is to establish a recoverable save point.**

1.  **Check for `task.md`**:
    *   If it exists, read it and follow its instructions.
    *   If it does not exist, you **must** create it immediately using the template below.
2.  **Create `task.md` from Template**: Copy the entire template below into a new file named `task.md`.
3.  **Submit `task.md`**: Use the `submit` tool to create a new branch and a pull request with this `task.md` file. This is your first "save point."

---

## `task.md` Template

```markdown
# Task: (User-defined task goal)

## Session Objective

The primary objective of this session is to follow the "Commit Early and Often" protocol to ensure all work is resilient and recoverable. All work will be performed on a single branch and PR, with `task.md` serving as the single source of truth.

## Working Branch & PR

*   **Branch**: `(the branch name for this session)`
*   **PR**: `(the URL of the pull request for this session)`

## Task Checklist

- [ ] (Task 1: Describe the first atomic change)
- [ ] (Task 2: Describe the second atomic change)
- [ ] (Task 3: etc...)

## Core Workflow

*   **One PR per Session**: All work for this objective is on the PR listed above.
*   **Atomic Commits**: Each item in the checklist is a single, logical change and will be its own commit.
*   **Commit via `submit`**: The only way to create commits is with the `submit` tool. Use it multiple times with the same branch name to add commits to the PR.
*   **Keep `task.md` Updated**: This `task.md` file must be updated and committed with every change. After completing a task, check it off, and add the update to your next commit.

## Git Workflow

The `run_in_bash_session` tool does not maintain a persistent git session. Do not use `git checkout` or `git commit` directly. Use the `submit` tool for all commits.
```
