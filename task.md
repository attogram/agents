# Task: Develop and Document the "Commit Early and Often" Protocol

## Session Objective

The primary objective of this session is to follow the "Commit Early and Often" protocol to ensure all work is resilient and recoverable. All work will be performed on a single branch and PR, with `task.md` serving as the single source of truth.

## Working Branch & PR

*   **Branch**: `feat/commit-early-protocol-v2`
*   **PR**: `(I will add the PR URL here once it is created)`

## Task Checklist

- [x] `1.0`: Establish the initial `AGENTS.commit-early-and-often.md` protocol document.
- [x] `1.1`: Add Bootstrap Protocol to instruct agents on how to start a session.
- [x] `1.2`: Refine the protocol to be more direct and actionable, including a `task.md` template.
- [x] `1.3`: Add the "User-Driven Completion" rule to the protocol.
- [x] `1.4`: Clarify the "Provisional Completion" rule.
- [x] `1.5`: Add a mandatory numbered format for the task checklist.
- [x] `1.6`: Explicitly forbid creating new branches or modifying the branch name.
- [ ] `2.0`: Create a `task.md` for the current session that accurately reflects the work done.
- [ ] `2.1`: Submit the session `task.md` to the existing PR.

## Core Workflow

*   **One PR per Session**: All work for this objective is on the PR listed above.
*   **Atomic Commits**: Each item in the checklist is a single, logical change and will be its own commit.
*   **Commit via `submit`**: The only way to create commits is with the `submit` tool. To add a subsequent commit to the existing pull request, you **must** use the `submit` tool with the **exact same branch name** used for the initial submission. Do not create a new branch. Do not modify the branch name in any way (e.g., by adding `-v2`).
*   **Keep `task.md` Updated**: This `task.md` file must be updated and committed with every change. After completing a task, check it off, and add the update to your next commit.
*   **Provisional Completion**: You are expected to mark tasks as complete (`[x]`) in the checklist as you finish them. However, this status is provisional. The user is the final arbiter of completion and may countermand your assessment.

## Git Workflow

The `run_in_bash_session` tool does not maintain a persistent git session. Do not use `git checkout` or `git commit` directly. Use the `submit` tool for all commits.
