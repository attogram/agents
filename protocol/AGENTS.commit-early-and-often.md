# AI Assistant Starter Prompt: Commit Early and Often

This document's sole purpose is to bootstrap a resilient working session for an AI assistant.

## Bootstrap Protocol

**Your first action in any new session is to establish a recoverable save point.**

1.  **Check for `task.md`**:
    *   If `task.md` exists, stop and read it. Follow its instructions to continue the existing task.
    *   If `task.md` does not exist, you **must** create it immediately by copying the template below.
2.  **Submit `task.md`**: After creating `task.md` from the template, use the `submit` tool to create a new branch and a pull request with the file. This is your first "save point." Then, ask the user for the high-level task.

---

## `task.md` Template (Copy into `task.md`)

```markdown
# Task: (To be defined by user)

## Session State

*   **Branch**: Use a short, descriptive, non-versioned name. **Anti-Pattern**: Do not use version numbers like `-v2` (e.g., `feat/commit-early-protocol-v2`). **Good Example**: `feat/establish-commit-protocol`.
*   **PR**: `(Fill in with the URL of the pull request for this session)`

---

## Protocol: Immutable Branch

**The branch created for this session is IMMUTABLE and PERSISTENT.**

*   **DO NOT CHANGE THE BRANCH.**
*   **DO NOT CREATE NEW BRANCHES.**

All subsequent work, including fixing errors, refining the protocol, or addressing user feedback, **must** be added as new commits to this single, original branch. Abandoning the branch is a critical protocol failure.

---

## Protocol: Core Workflow

*   **Task Checklist**: All work must be broken down into a numbered checklist (e.g., `1.1`, `1.1.1`) to allow for precise referencing. This is the primary work log.
*   **Atomic Commits**: Each numbered item in the checklist is a single, logical change and will be its own commit.
*   **Keep `task.md` Updated**: This `task.md` file must be updated and committed with every change. After completing a task, check it off (`[x]`).
*   **Provisional Completion**: You are expected to mark tasks as complete. However, this status is provisional. The user is the final arbiter of completion.
*   **Neutral Commit Language**: Do not use words that imply finality (e.g., "final", "done", "complete") in commit messages or PR descriptions. All work is provisional until approved by the user.

---

## Protocol: Git Workflow

*   **Commit via `submit`**: The only way to create commits is with the `submit` tool.
*   **Adding Commits**: To add a subsequent commit to the existing pull request, you **must** use the `submit` tool with the **exact same branch name** used for the initial submission.
*   **`run_in_bash_session` Warning**: The `run_in_bash_session` tool does not maintain a persistent git session. Do not use `git checkout` or `git commit` directly.

---

## Task Checklist

- [ ] `1.0`: Create this `task.md` file.
- [ ] `1.1`: Submit this `task.md` file to a new branch to establish the session PR.
```
