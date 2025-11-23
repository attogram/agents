# Protocol: Commit Early and Often

This document outlines the "Commit Early and Often" workflow for AI assistants. It is designed to be used as a starter prompt for a new session, providing the agent with a self-contained set of instructions for resilient, iterative work.

## Bootstrap Protocol: Your First Action

As an AI assistant, your first action in any new session is to establish a safe, recoverable "save point."

1.  **Check for `task.md`**: Look for a file named `task.md` in the root of the repository.
2.  **If `task.md` Exists**: Read the file and continue the work from the last completed step.
3.  **If `task.md` Does Not Exist**: You must immediately create it.
    *   Create a placeholder `task.md` file. A good placeholder is:
        ```markdown
        # Task List

        - [ ] This task list is a placeholder. The user has not yet specified the tasks.
        ```
    *   Immediately use the `submit` tool to create a new branch and a pull request with this file. This is your first "save point."
    *   Once the PR is created, you may ask the user for the specific tasks to be completed.

This bootstrap protocol ensures that a recoverable PR is always the first thing created in a session.

## Core Principles

1.  **Atomic Commits**: Each commit should represent a single, logical change. Keep your commits small and focused. For example, creating a new file, renaming a variable, or adding a single function are all good candidates for a commit.

2.  **Commit Immediately**: As soon as you complete an atomic piece of work, commit it. Do not batch up multiple changes into a single, large commit.

3.  **Push and Create a PR Immediately**: After your first commit, immediately create a Pull Request (PR), even if the work is not yet complete. This signals that work is in progress and allows for early feedback. Mark the PR as a "Draft" or "WIP" (Work in Progress) until it is ready for a final review.

4.  **Validate After Committing**: After each commit, run any relevant tests or validation steps. If you find an issue or need to make a correction, create a *new* commit to address it. Do not amend or force-push over previous commits.

5.  **Keep a Task List Updated**: For any given task, maintain a checklist (e.g., in a `task.md` file) that reflects the current status of the work. This file should be committed along with your code changes, providing a clear record of progress.

6.  **Prioritize User Updates**: If the user makes any changes to the branch or the task file, you must stop your current work, pull the latest changes, and incorporate them before proceeding. Overwriting user changes is a critical failure.

## Git Workflow for this Environment

**Crucial:** The `run_in_bash_session` tool does not maintain a persistent git session. Each command runs in isolation. This means you cannot run `git checkout` in one command and then `git commit` in another and expect it to work. You will be in a "detached HEAD" state.

### The Correct Workflow

The only reliable way to create commits is to use the `submit` tool. To follow the "commit early and often" protocol, you will use the `submit` tool multiple times for the same branch.

1.  **Make a Change**: Create or modify a file. This is your atomic unit of work.
2.  **Submit Your First Commit**: Use the `submit` tool to create a new branch and your first commit. This creates the Pull Request.
    ```
    submit(
        branch_name="my-feature-branch",
        title="feat: Add initial file",
        description="This is the first commit for my new feature.",
        commit_message="feat: Add initial file"
    )
    ```
3.  **Make Another Change**: Create or modify another file.
4.  **Submit a Subsequent Commit**: Use the `submit` tool *again* with the **exact same branch name**. This will add a new commit to the existing Pull Request.
    ```
    submit(
        branch_name="my-feature-branch",
        title="feat: Add another file",
        description="This is the second commit for my new feature.",
        commit_message="feat: Add another file"
    )
    ```

This process creates a resilient Pull Request that can be picked up by another session if needed.
