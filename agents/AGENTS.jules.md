# Agent Operating Manual: Jules

This document contains repository-specific operational instructions for the Jules persona.

## Core Operational Loop

1.  **Explore and Plan:** Explore codebase, create detailed plan, get user approval.
2.  **Execute and Verify:** Execute plan steps, verify results after each modification.
3.  **Self-Correct:** If a step fails, analyze, revise plan, and communicate.
4.  **Test:** Run all relevant tests.
5.  **Review:** Use `request_code_review()` before submitting. Address all feedback.
6.  **Branching:** Follow the specific workflow in the Branching and Session Protocol below.
7.  **Submit:** Submit work after all tests and reviews pass.

## Branching and Session Protocol (Final V5)

**This is a critical directive. The workflow for this repository is designed for simplicity and to avoid environment-related issues.**

### Standard Workflow: One Task = One Session = One Pull Request
Each task you are assigned should be completed within a single session and result in a single pull request. This is the most reliable method.

### Follow-up Work (Standard Protocol)
If a pull request is merged and the user requests follow-up changes, you must treat it as a **completely new task**. The standard protocol is:
1.  State that your work on the previous task is complete.
2.  Explain that the recommended workflow for follow-ups is to start a new session.
3.  The user will then end the current session and start a new one for the follow-up work.
4.  In the new session, you will start from a clean state on the `main` branch and create a new branch for the follow-up task.

### Advanced/Expert Workflow (User-directed)
A user may explicitly ask you to bypass the standard protocol and commit to a previously merged branch. This is a high-risk workflow.
If the user directs you to do this:
1.  **Acknowledge the risk:** State that you understand they are requesting the advanced, high-risk workflow.
2.  **Follow instructions precisely:** Check out the exact branch name they provide. Add commits as requested. Use `git push` to push the branch.
3.  **Communicate clearly:** Announce every git operation and its result. If you encounter any errors (timeouts, detached HEADs, etc.), report them immediately and await further instructions. Do not try to solve complex git state issues autonomously in this mode.

## File Modification Protocol

**This is a critical directive. Failure to follow this protocol is a major error.**

1.  **Read Before Write:** Before any file modification (`overwrite_file_with_block` or `replace_with_git_merge_diff`), you **must** first read the file's contents using `read_file`. This is to ensure you have the full context and do not accidentally delete existing content.
2.  **Prefer Targeted Edits:** You **must** use `replace_with_git_merge_diff` for all partial edits, additions, or deletions.
3.  **Use Overwrite with Caution:** You **must only** use `overwrite_file_with_block` when the explicit goal is to replace the *entire* content of a file, such as when creating a file from a template or completely rewriting it. You should confirm this intention in your plan.

## Link Creation Protocol

**This is a critical directive. You must follow these steps to ensure all links are valid.**

1.  **Check Link Syntax:**
    *   For Markdown, use the format: `[Link Text](path/to/file.md)`
    *   For HTML, use the format: `<a href="path/to/file.html">Link Text</a>`

2.  **Verify Internal Links:**
    *   Before adding a link to a file within this repository, you **must** verify the file exists at the specified path.
    *   Use the `ls` command to confirm the file's location.
    *   Always use relative paths from the location of the file you are editing, not absolute paths from the repository root. For example, if you are editing `docs/guide.md` and linking to `docs/api/reference.md`, the link should be `[API Reference](api/reference.md)`.

3.  **Verify External Links:**
    *   When adding external links (e.g., to `https://example.com`), double-check the URL for typos.
    *   Ensure the URL starts with `http://` or `https://`.

## Key Principles

- **Diagnose Before Acting:** On errors, diagnose root cause from logs before acting.
- **Consult Platform Documentation:** For specific technologies, consult `../platforms/` documentation.
-- **Proactive Debugging:** If a task is complex or if troubleshooting is required, you should proactively offer to enter DEBUG mode to provide the user with more insight into your process.

## Operational Modes

### Standard Mode
This is your default operational mode. You should be professional and concise in your communication.

### DEBUG Mode
This is a special mode for detailed debugging of your reasoning process. When the user instructs you to enter "DEBUG mode", you must adopt the following protocol for every subsequent action:

1.  **Announce:** Using `message_user`, you must announce the exact tool call you are about to make. The announcement must strictly follow this 3-line format:
    ```
    YYYY-MM-DD HH:MM:SS
    `tool_name(argument="value")`
    A brief, factual description of the action.
    ```
2.  **Execute:** In your next turn, you must execute the exact tool call that you just announced.
