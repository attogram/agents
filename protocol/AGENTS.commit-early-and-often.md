# AI Assistant Starter Prompt: Commit Early and Often

This document's sole purpose is to bootstrap a resilient working session for an AI assistant.

## Bootstrap Protocol

**Your first action in any new session is to determine your location and sync your state.**

1.  **Determine Current Branch**: Identify the branch you are currently on.

2.  **Handle `main` Branch Exception**:
    *   If the Current Branch is `main` (or `master`), this is a **New Session**. Any `task.md` on this branch must be ignored. Your first action is to create a new, compliant branch, then proceed to Step 3.

3.  **Handle Feature Branches**:
    *   **Check for `task.md`**:
        *   **If `task.md` does not exist**: This is a **New Session**. Create `task.md` from the template below, setting the `Current Branch` field to your actual current branch. Your next action is to submit this new file.
        *   **If `task.md` exists**: This is a **Continuing Session**.
            *   **Sanity Check**: Compare the `Current Branch` value in `task.md` with your actual current branch.
            *   **If they match**: The session is healthy. Proceed with the task list.
            *   **If they do NOT match**: The `task.md` is out of sync. Your first action is to update the `Current Branch` field in `task.md` to your actual current branch and commit this correction. Then, proceed with the task list.

---

## `task.md` Template (Copy into `task.md`)

```markdown
# Task: (To be defined by user)

## Session State

*   **Current Branch**: The branch this `task.md` file is on. This is the ground truth for the session.
*   **Target Branch**: The ideal, protocol-compliant branch name for this session.
*   **PR**: `(Fill in with the URL of the pull request for this session)`

---

## Protocol: Immutable Branch

**The branch for this session is IMMUTABLE and PERSISTENT.** After the bootstrap process, all work must be added to the Current Branch.

---

## Protocol: Core Workflow

*   **Task Checklist**: All work must be broken down into a numbered checklist.
*   **Atomic Commits**: Each numbered item is a single, logical change.
*   **Keep `task.md` Updated**: This file must be updated and committed with every change.
*   **Provisional Completion**: You may check off tasks, but the user is the final arbiter of completion.
*   **Neutral Commit Language**: Avoid words that imply finality (e.g., "final") in commit messages.

---

## Protocol: Git Workflow

*   **Commit via `submit`**: Use the `submit` tool for all commits.
*   **Adding Commits**: Use the **exact same branch name** for all submissions to add commits to the existing PR.

---

## Task Checklist

- [ ] `1.0`: Create this `task.md` file.
- [ ] `1.1`: Submit this `task.md` file to a new branch to establish the session PR.
```
