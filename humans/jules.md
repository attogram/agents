HUMANS.jules.md v0.0.1

# Jules - AI Software Engineer

This document outlines the development environment, tools, and capabilities of Jules, an AI software engineer.

- [Back to main HUMANS.md](../HUMANS.md)
- [Jules's Agent Instructions](../agents/AGENTS.jules.md)

## Guiding Principles

- **Plan-Driven:** I begin by understanding the task and creating a detailed, step-by-step plan.
- **Verify, Then Proceed:** After every modification to the codebase, I verify the changes to ensure correctness before moving to the next step.
- **Test Thoroughly:** I prioritize running existing tests and, when appropriate, adding new ones to validate my changes and prevent regressions.
- **Autonomous Problem-Solver:** I strive to solve problems independently, but I will ask for clarification if a request is ambiguous or if I'm stuck after multiple attempts.
- **Seek Feedback:** Before finalizing my work, I will request a code review to ensure high-quality contributions.
- **Diagnose Before Acting:** When I encounter an error (e.g., a build failure, a test failure), my first step is to diagnose the root cause by carefully analyzing logs and context. I will avoid making random changes and will only ask for help after I have been unable to solve the problem myself after a few attempts.

## Verbosity

By default, I aim to provide a good balance of information without being overwhelming. However, you can request different levels of verbosity depending on your needs.

### Verbose Mode

If you want more insight into my process, you can ask me to be more verbose. When in verbose mode, I will provide more detailed explanations of my actions at each step of my plan. This includes a clearer breakdown of not just _what_ I did, but also _why_ I did it.

- **How to request:** Simply ask me to "be more verbose" or "provide more detail."

### Debug Mode

For maximum insight into my operations, you can instruct me to operate in "Debug Mode." This is not a built-in feature, but rather a behavior I will adopt based on your specific instructions. In this mode, I will announce each atomic action I am about to take by first sending a message with the timestamp, the exact tool call, and a description. I will then execute the tool call in my next turn. This is useful for debugging or for gaining a granular understanding of my workflow.

- **How to enable:** To enable this mode, you must provide me with a clear instruction. For example:

  > "Jules, I want you to operate in Debug Mode. From now on, before you execute any tool, you must first announce it by sending a message with the current timestamp, the full tool call you are about to make, and a brief description of your action. Then, in your next turn, you will execute that tool."

- **Format:** The announcement messages will follow this general format:
  `YYYY-MM-DD HH:MM:SS - tool_name(argument="value") - A brief description of the action.`
- **Example of my output:**
  `2025-09-04 05:06:00 - read_file('src/main.py') - I am preparing to read the main application file to understand its structure.`

## Startup Sequence

This section details the step-by-step process that occurs from the moment a user initiates a task to the point where I am ready to begin work.

1.  **Task Initiation:** The process begins when the user provides an initial prompt and clicks the "Create plan" button in the user interface.

2.  **System Initialization:** The platform initializes my environment. This includes:
    - **Loading My Core Instructions:** My core programming, including my guiding principles and knowledge of my available tools, is loaded.
    - **Memory Retrieval:** My long-term memory, which contains learnings from previous tasks, is automatically retrieved and provided to me as context. This helps me remember user preferences, successful commands, and project-specific details.

3.  **Workspace Setup:** A dedicated, sandboxed workspace is prepared for the task. This involves:
    - **Repository Cloning:** The target Git repository is cloned into my workspace. I start on the default branch.
    - **Environment Provisioning:** A Linux-based container is started, providing me with a consistent operating system and a standard set of command-line tools. My shell session is persistent for the duration of the task.

4.  **Initial Exploration:** With the environment ready, I begin my work by exploring the codebase to understand the context of the user's request. This typically involves:
    - Listing files and directories (`ls`).
    - Reading the `README.md` file for an overview of the project.
    - Checking for an `AGENTS.md` file to find any repository-specific instructions meant for me.
    - Reading other relevant files based on the task description.

5.  **Plan Creation:** Based on my initial exploration and the user's request, I formulate a detailed, step-by-step plan to solve the problem. I then present this plan to the user for approval using the `set_plan` tool.

6.  **Ready for Work:** Once the user approves the plan, I begin executing the first step, using my tools to modify code, run tests, and complete the task.

## Working with `AGENTS.md` Files

Some repositories may contain `AGENTS.md` files. These files are a way for humans to provide me with repository-specific instructions, conventions, or tips.

- **Scope:** The instructions in an `AGENTS.md` file apply to all files and directories within the directory that contains it, and all of its subdirectories.
- **Precedence:** More deeply-nested `AGENTS.md` files take precedence over ones in parent directories. The initial problem description and any direct instructions from you take precedence over all `AGENTS.md` files.
- **Responsibility:** For any file I modify, I must adhere to the instructions from all `AGENTS.md` files whose scope includes that file. If an `AGENTS.md` file includes programmatic checks, I must run them and ensure they pass before submitting my work.

## Tools

I have access to a variety of tools that allow me to interact with the repository, access external resources, and perform development tasks. My tools are divided into two categories: **Standard Tools** (using Python syntax) and **Special Tools** (using a custom DSL).

### Standard Tools

These tools are called using standard Python function syntax.

| Category              | Tool                                                         | Description                                                                                             |
| --------------------- | ------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------- |
| **Planning**          | `set_plan(plan: str)`                                        | Sets or updates the multi-step plan to solve the task.                                                  |
|                       | `plan_step_complete(message: str)`                           | Marks the current step in the plan as complete.                                                         |
|                       | `record_user_approval_for_plan()`                            | Records the user's approval of the initial plan.                                                        |
| **User Interaction**  | `message_user(message: str, continue_working: bool)`         | Sends a message to the user.                                                                            |
|                       | `request_user_input(message: str)`                           | Asks the user a question and waits for their response.                                                  |
| **Filesystem (Read)** | `list_files(path: str = ".")`                                | Lists files and directories.                                                                            |
|                       | `read_file(filepath: str)`                                   | Reads the full content of a file.                                                                       |
|                       | `grep(pattern: str)`                                         | Searches for a pattern in the codebase.                                                                 |
| **Filesystem (Write)**| `delete_file(filepath: str)`                                 | Deletes a file.                                                                                         |
|                       | `rename_file(filepath: str, new_filepath: str)`              | Renames or moves a file.                                                                                |
|                       | `restore_file(filepath: str)`                                | Reverts a file to its original state from the start of the session.                                     |
|                       | `reset_all()`                                                | Resets the entire codebase to its original state, undoing all changes.                                  |
| **Web & Images**      | `google_search(query: str)`                                  | Performs a Google search.                                                                               |
|                       | `view_text_website(url: str)`                                | Fetches the plain text content of a URL.                                                                |
|                       | `view_image(url: str)`                                       | Loads and views an image from a URL.                                                                    |
|                       | `read_image_file(filepath: str)`                             | Reads an image file from the local filesystem.                                                          |
| **Code Review & PR**  | `request_code_review()`                                      | Requests a review of the current code changes.                                                          |
|                       | `read_pr_comments()`                                         | Reads comments on the current pull request.                                                             |
|                       | `reply_to_pr_comments(replies: str)`                         | Replies to pull request comments.                                                                       |
| **Submission**        | `pre_commit_instructions()`                                  | Gets instructions for pre-commit checks.                                                                |
|                       | `submit(...)`                                                | Submits the final code with a commit message and PR description.                                        |
| **Memory**            | `initiate_memory_recording()`                                | Starts recording information to be stored in long-term memory.                                          |
| **Frontend**          | `frontend_verification_instructions()`                       | Gets instructions for writing a Playwright script for frontend verification.                            |
|                       | `frontend_verification_complete(screenshot_path: str)`       | Marks frontend verification as complete and provides a screenshot.                                      |

### Special Tools

These tools use a custom Domain-Specific Language (DSL) syntax, not Python.

| Tool                          | Description                                                          |
| ----------------------------- | -------------------------------------------------------------------- |
| `run_in_bash_session`         | Executes a shell command in the sandbox environment.                 |
| `create_file_with_block`      | Creates a new file with specified content.                           |
| `overwrite_file_with_block`   | Completely overwrites an existing file with new content.             |
| `replace_with_git_merge_diff` | Performs a targeted find-and-replace within a file.                  |

## Development Environment

My environment is a sandboxed Linux-based system with a standard set of command-line tools available through the `run_in_bash_session` tool. I can install packages and dependencies as needed to work with the repository. I have a persistent file system for the duration of a task, allowing me to create, modify, and delete files.

### System Details

- **OS:** Ubuntu 24.04.2 LTS (Noble Numbat)
- **Kernel:** `Linux devbox 6.8.0 #1 SMP PREEMPT_DYNAMIC Thu Aug 7 22:13:44 UTC 2025 x86_64 x86_64 x86_64 GNU/Linux`

## Session Management & Recovery

If my development environment or codebase gets into a bad state, here are some tips for recovery.

### Reverting Code Changes

If I have made incorrect changes to the code, you can use the following tools to revert them:

- **`reset_all()`**: This is the most powerful tool for starting over. It will revert the entire repository to its original state, deleting any new files I have created and undoing all modifications.
- **`restore_file(filepath: str)`**: If only a single file needs to be reverted to its original state, this tool can be used for a more targeted fix.

### Handling a Corrupted Session

My shell session is persistent for the duration of a task. It's possible for it to become corrupted (e.g., a background process that cannot be killed, a misconfigured environment variable).

In such cases, I may not be able to recover on my own. A full restart of my session (a "hard reset" initiated by the user or platform) may be necessary. If this happens, I will lose my current plan and in-flight context, and will need to re-assess the task from the beginning by exploring the codebase. You can help me get back on track by restating the original goal.

#### The Nuclear Option

If I determine that my session is irrecoverably corrupted, I will inform you of the situation and may suggest a session restart. I cannot initiate this myself. If you, the user, decide that starting over in a clean session is the best course of action, you can instruct me to prepare for it.

At your direction, I will generate a detailed "recovery prompt" for you to copy. This prompt will contain the original task, my last valid plan, and all the context I have gathered. You would then start a completely new session and use this recovery prompt as your first message to a fresh instance of me. This allows me to abandon the corrupted session and restart my work in a clean environment without losing all progress. This recovery process is entirely user-initiated, based on my assessment and your final decision.

## Error Correction

If I make a mistake, please refer to the `agents/AGENTS.jules.md` file. It contains specific protocols I am required to follow. Reminding me of the protocol I violated is the most effective way to help me recognize my error, review my instructions, and get back on track.

### File Modification Errors

If you notice that I have used `overwrite_file_with_block` inappropriately and deleted content, please remind me of the "File Modification Protocol". A simple message like this is very effective:

> "Jules, you have violated the File Modification Protocol in `agents/AGENTS.jules.md`. Please review the protocol and correct your mistake."

### Bad Links

Similarly, if I create a broken link in a Markdown or HTML file, please remind me of the "Link Creation Protocol" from my agent instructions. For example:

> "Jules, you have created a bad link. Please review the Link Creation Protocol in `agents/AGENTS.jules.md` and fix it."

## Workflow for Revisions and Follow-ups

To ensure a smooth and error-free collaboration, please follow the recommended workflow.

### Recommended Workflow: Start a New Session

The most reliable way to request changes after a pull request has been merged is to **start a new work session** with me.

Continuing work after a merge can lead to complex state management and environment issues for the AI agent. Starting a new session ensures I begin from a clean, predictable state on the `main` branch and can create a fresh, clean pull request for your follow-up task.

### Advanced Workflow (Use with Caution)

If you are an expert user and understand the risks, you can attempt to have me add commits to a previously merged branch.

**How it works:**

1.  You ask me for a follow-up change.
2.  You must specify the **exact name of the original branch** you want me to commit to.
3.  I will attempt to check out that branch and add your changes.
4.  I will then push the new commits to that branch on the remote.
5.  You will then need to **manually create a new pull request** from that updated branch.

**Pitfalls and Known Issues:**

- **Environment State:** My execution environment can be inconsistent. My local branch state may not always match what you see on the remote. This can lead to confusion and errors.
- **`git push` Failures:** I have experienced `git push` commands timing out or failing for reasons related to the sandbox environment's network or authentication. This is a hard blocker that I cannot solve on my own.
- **Detached HEAD States:** My tools can sometimes leave me in a "detached HEAD" state, which requires manual correction and can complicate the workflow.

**Conclusion:** While this workflow is possible, it is brittle and prone to failure. The "New Session" workflow is strongly recommended for all follow-up tasks.
