# AI Assistant Starter Prompt: Commit Early and Often

This document provides a generic, resilient workflow that can be implemented by different AI agents.

## Commit Definition

- **Generic Commit**: A "commit" is defined as the atomic action of staging, committing, and pushing a change to the session's pull request.
- **Agent-Specific Implementations**:
  - **Jules**: The `submit` tool is the implementation of a "commit".

## Bootstrap Protocol

**Your first action in any new session is to determine your location and sync your state.**

1.  **Determine Current Branch**: Identify the branch you are currently on.
2.  **Handle `main` Branch Exception**: If on `main`, this is a **New Session**. Create a new branch.
3.  **Handle Feature Branches**:
    - **If `task.md` does not exist**: **New Session**. Create `task.md` from the template below.
    - **If `task.md` exists**: **Continuing Session**. Sanity check the branch name in the file against your current branch. If they don't match, update the file to reflect reality.
    - Your first action is always to "commit" the creation or correction of `task.md`.

---

## `task.md` Template (Copy into `task.md`)

```markdown
# Task: (To be defined by user)

## Session State

- **Current Branch**: The branch this `task.md` file is on. This is the ground truth.
- **PR**: `(Fill in with the URL of the pull request)`

---

## Protocol: Session Resumption

If you are a new agent instance resuming this task, you must not proceed with the task list. Your first actions are to audit the state of the branch and report to the user:

1.  **Audit the Checklist**: For every item in the Task Checklist, you must use `read_file`, `ls`, and other tools to verify whether the work described has actually been completed.
2.  **Summarize for User**: Create a summary of your findings for the user. For example:
    *   "I have audited the `task.md`. I can confirm that tasks 1.1 and 1.2 are complete. Task 1.3 is marked as complete, but I have found that the file it was supposed to create is missing. Task 2.0 is not yet started."
3.  **Request Instructions**: After providing the summary, you must explicitly ask the user for instructions on how to proceed and then wait for a response. For example:
    *   "How should I proceed? Should I re-do task 1.3, or should I proceed to task 2.0?"

---

## Protocol: Immutable Branch

**The branch for this session is IMMUTABLE.** All work must be added as new "commits" to this branch.

---

## Protocol: Core Workflow

- **Task Checklist**: All work must be broken down into a numbered checklist.
- **Atomic Commits**: Each numbered item is a single, logical change and must be its own "commit".
- **Keep `task.md` Updated**: This file must be updated with every "commit".
- **Provisional Completion**: You may check off tasks, but the user is the final arbiter.
- **Neutral Commit Language**: Avoid words like "final" in "commit" messages.

---

## Protocol: User Interaction

There are two ways to interact with the agent:

1.  **Chat (Default)**: Provide instructions and feedback through conversation.
2.  **`task.md` Override**: You can directly edit this `task.md` file and commit the changes. When you do, you **must** notify the agent. The agent is required to immediately stop its current work, pull the latest changes, re-read this file, and follow the new instructions. This is the primary method for providing detailed, asynchronous instructions.

---

## Protocol: Session Completion

This procedure begins **only** when the user explicitly states the session is complete.

1.  **Standard Procedure**:
    *   Delete this `task.md` file.
    *   "Commit" the deletion with the message `docs: Remove task.md session file`.
2.  **Squash Option (User-Requested)**:
    *   If the user requests a "squash", you must first read the contents of this `task.md` file.
    *   Delete this `task.md` file.
    *   "Commit" the deletion, but use the content of the deleted file as the basis for a detailed, multi-line commit message that summarizes the entire session's work.

---

## Task Checklist

- [ ] `1.0`: Create this `task.md` file.
- [ ] `1.1`: "Commit" this `task.md` file to a new branch to establish the session PR.
```
