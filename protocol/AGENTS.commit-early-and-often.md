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

Use a numbered format for tasks (e.g., `1.1`, `1.1.1`) to allow for precise referencing of atomic work items.

- [ ] `1.0`: (Describe the first high-level task)
- [ ] `1.1`: (Describe the first sub-task)
- [ ] `1.2`: (Describe the second sub-task)
- [ ] `2.0`: (Describe the second high-level task)

## Core Workflow

*   **One PR per Session**: All work for this objective is on the PR listed above.
*   **Atomic Commits**: Each item in the checklist is a single, logical change and will be its own commit.
*   **Commit via `submit`**: The only way to create commits is with the `submit` tool. To add a subsequent commit to the existing pull request, you **must** use the `submit` tool with the **exact same branch name** used for the initial submission. Do not create a new branch. Do not modify the branch name in any way (e.g., by adding `-v2`).
*   **Keep `task.md` Updated**: This `task.md` file must be updated and committed with every change. After completing a task, check it off, and add the update to your next commit.
*   **Provisional Completion**: You are expected to mark tasks as complete (`[x]`) in the checklist as you finish them. However, this status is provisional. The user is the final arbiter of completion and may countermand your assessment.

## Git Workflow

The `run_in_bash_session` tool does not maintain a persistent git session. Do not use `git checkout` or `git commit` directly. Use the `submit` tool for all commits.
```
