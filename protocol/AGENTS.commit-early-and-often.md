# Protocol: Commit Early and Often

This document is a starter prompt for AI assistants. It defines a resilient, iterative workflow.

## Bootstrap Protocol

**Your first action in any new session is to establish a recoverable save point.**

1.  **Check for `task.md`**:
    *   If it exists, read it and continue the task.
    *   If it does not exist, you **must** create it immediately using the template below.
2.  **Create `task.md` from Template**:
    ```markdown
    # Task File

    ## Session Objective

    *   **User Goal**: (Describe the user's high-level goal here)
    *   **Agent's Role**: (Describe the agent's role in achieving this goal)

    ## Working Branch & PR

    *   **Branch**: `(the branch name for this session)`
    *   **PR**: `(the URL of the pull request for this session)`

    ## Task Checklist

    - [ ] (Task 1)
    - [ ] (Task 2)
    - [ ] (Task 3)

    ## Recovery Notes

    This file is the single source of truth for this session. If the session is interrupted, a new agent can use this file to understand the goal, find the branch and PR, and continue the work from the last completed task.
    ```
3.  **Submit the `task.md` File**: Immediately use the `submit` tool to create a new branch and a pull request with this file. This is your first "save point."

## Core Workflow

*   **One PR per Session**: All work for a single objective should be on a single PR.
*   **Atomic Commits**: Each logical change is a separate commit.
*   **Commit via `submit`**: The only way to create commits is with the `submit` tool. Use it multiple times with the same branch name to add commits to the PR.
*   **Keep `task.md` Updated**: `task.md` must be updated and committed with every change. It is the recovery log.

## Git Workflow

The `run_in_bash_session` tool does not maintain a persistent git session. Do not use `git checkout` or `git commit` directly. Use the `submit` tool for all commits.
