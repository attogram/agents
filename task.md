# Task: Develop and Document the "Commit Early and Often" Protocol

## Session State

*   **Branch**: `feat/commit-early-protocol-v2` (Note: This name is non-compliant and serves as a lesson for the protocol.)
*   **PR**: `(I will add the PR URL here after the next submission)`

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

---

## Protocol: Git Workflow

*   **Commit via `submit`**: The only way to create commits is with the `submit` tool.
*   **Adding Commits**: To add a subsequent commit to the existing pull request, you **must** use the `submit` tool with the **exact same branch name** used for the initial submission.
*   **`run_in_bash_session` Warning**: The `run_in_bash_session` tool does not maintain a persistent git session. Do not use `git checkout` or `git commit` directly.

---

## Task Checklist

- [x] `1.0`: Establish the initial `AGENTS.commit-early-and-often.md` protocol document.
- [x] `1.1`: Add Bootstrap Protocol to instruct agents on how to start a session.
- [x] `1.2`: Refine the protocol to be more direct and actionable, including a `task.md` template.
- [x] `1.3`: Add the "User-Driven Completion" rule to the protocol.
- [x] `1.4`: Clarify the "Provisional Completion" rule.
- [x] `1.5`: Add a mandatory numbered format for the task checklist.
- [x] `1.6`: Explicitly forbid creating new branches or modifying the branch name.
- [x] `1.7`: Fortify the protocol with the "Immutable Branch Principle".
- [x] `1.8`: Consolidate the entire protocol into the `task.md` template, making the AGENTS file a pure bootstrap installer.
- [x] `1.9`: Add a specific anti-pattern warning for branch naming, using the current branch as a lesson.
- [ ] `2.0`: Create this comprehensive `task.md` file, documenting all protocol refinements.
- [ ] `2.1`: Submit the final protocol and this `task.md` together in a single, compliant commit.
