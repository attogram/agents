# AI Assistant Starter Prompt: Commit Early and Often

This document provides a generic, resilient workflow that can be implemented by different AI agents.

## Commit Definition

*   **Generic Commit**: A "commit" is defined as the atomic action of staging, committing, and pushing a change to the session's pull request.
*   **Agent-Specific Implementations**:
    *   **Jules**: The `submit` tool is the implementation of a "commit".

## Bootstrap Protocol

**Your first action in any new session is to determine your location and sync your state.**

1.  **Determine Current Branch**: Identify the branch you are currently on.
2.  **Handle `main` Branch Exception**: If on `main`, this is a **New Session**. Create a new branch.
3.  **Handle Feature Branches**:
    *   **If `task.md` does not exist**: **New Session**. Create `task.md` from the template below.
    *   **If `task.md` exists**: **Continuing Session**. Sanity check the branch name in the file against your current branch. If they don't match, update the file to reflect reality.
    *   Your first action is always to "commit" the creation or correction of `task.md`.

---

## `task.md` Template (Copy into `task.md`)

```markdown
# Task: (To be defined by user)

## Session State

*   **Current Branch**: The branch this `task.md` file is on. This is the ground truth.
*   **PR**: `(Fill in with the URL of the pull request)`

---

## Protocol: Session Resumption

If you are a new agent instance resuming this task, your first actions are:
1.  Verify the completion of the last checked-off item in the Task Checklist.
2.  Add a new item to the checklist: `X.0: Resume session and verify state`.
3.  Check off this new item.
4.  "Commit" the updated `task.md`. This logs the handover. Then, proceed with the remaining tasks.

---

## Protocol: Immutable Branch

**The branch for this session is IMMUTABLE.** All work must be added as new "commits" to this branch.

---

## Protocol: Core Workflow

*   **Task Checklist**: All work must be broken down into a numbered checklist.
*   **Atomic Commits**: Each numbered item is a single, logical change and must be its own "commit".
*   **Keep `task.md` Updated**: This file must be updated with every "commit".
*   **Provisional Completion**: You may check off tasks, but the user is the final arbiter.
*   **Neutral Commit Language**: Avoid words like "final" in "commit" messages.

---

## Task Checklist

- [ ] `1.0`: Create this `task.md` file.
- [ ] `1.1`: "Commit" this `task.md` file to a new branch to establish the session PR.
```
