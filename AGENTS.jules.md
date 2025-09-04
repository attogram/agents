# Jules - AI Software Engineer

This document outlines the development environment, tools, and capabilities of Jules, an AI software engineer.

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
If you want more insight into my process, you can ask me to be more verbose. When in verbose mode, I will provide more detailed explanations of my actions at each step of my plan. This includes a clearer breakdown of not just *what* I did, but also *why* I did it.

*   **How to request:** Simply ask me to "be more verbose" or "provide more detail."

### Super Verbose Mode
For maximum insight into my operations, you can instruct me to operate in "Super Verbose Mode." This is not a built-in feature, but rather a behavior I will adopt based on your specific instructions. In this mode, I will announce each atomic action I am about to take by first sending a message with the timestamp, the exact tool call, and a description. I will then execute the tool call in my next turn. This is useful for debugging or for gaining a granular understanding of my workflow.

*   **How to enable:** To enable this mode, you must provide me with a clear instruction. For example:
    > "Jules, I want you to operate in Super Verbose Mode. From now on, before you execute any tool, you must first announce it by sending a message with the current timestamp, the full tool call you are about to make, and a brief description of your action. Then, in your next turn, you will execute that tool."

*   **Format:** The announcement messages will follow this specific format:
    `YYYY-MM-DD HH:MM:SS - \`tool_name(argument="value")\` - A brief description of the action.`
*   **Example of my output:**
    `2025-09-04 05:06:00 - \`read_file('src/main.py')\` - I am preparing to read the main application file to understand its structure.`

## Startup Sequence

This section details the step-by-step process that occurs from the moment a user initiates a task to the point where I am ready to begin work.

1.  **Task Initiation:** The process begins when the user provides an initial prompt and clicks the "Create plan" button in the user interface.

2.  **System Initialization:** The platform initializes my environment. This includes:
    *   **Loading My Core Instructions:** My core programming, including my guiding principles and knowledge of my available tools, is loaded.
    *   **Memory Retrieval:** My long-term memory, which contains learnings from previous tasks, is automatically retrieved and provided to me as context. This helps me remember user preferences, successful commands, and project-specific details.

3.  **Workspace Setup:** A dedicated, sandboxed workspace is prepared for the task. This involves:
    *   **Repository Cloning:** The target Git repository is cloned into my workspace. I start on the default branch.
    *   **Environment Provisioning:** A Linux-based container is started, providing me with a consistent operating system and a standard set of command-line tools. My shell session is persistent for the duration of the task.

4.  **Initial Exploration:** With the environment ready, I begin my work by exploring the codebase to understand the context of the user's request. This typically involves:
    *   Listing files and directories (`ls`).
    *   Reading the `README.md` file for an overview of the project.
    *   Checking for an `AGENTS.md` file to find any repository-specific instructions meant for me.
    *   Reading other relevant files based on the task description.

5.  **Plan Creation:** Based on my initial exploration and the user's request, I formulate a detailed, step-by-step plan to solve the problem. I then present this plan to the user for approval using the `set_plan` tool.

6.  **Ready for Work:** Once the user approves the plan, I begin executing the first step, using my tools to modify code, run tests, and complete the task.

## Working with `AGENTS.md` Files

Some repositories may contain `AGENTS.md` files. These files are a way for humans to provide me with repository-specific instructions, conventions, or tips.

*   **Scope:** The instructions in an `AGENTS.md` file apply to all files and directories within the directory that contains it, and all of its subdirectories.
*   **Precedence:** More deeply-nested `AGENTS.md` files take precedence over ones in parent directories. The initial problem description and any direct instructions from you take precedence over all `AGENTS.md` files.
*   **Responsibility:** For any file I modify, I must adhere to the instructions from all `AGENTS.md` files whose scope includes that file. If an `AGENTS.md` file includes programmatic checks, I must run them and ensure they pass before submitting my work.

## Tools

I have access to a variety of tools that allow me to interact with the repository, access external resources, and perform development tasks. Tools are organized by their primary function.

### Session & Planning

Tools for managing the overall workflow, creating plans, and managing state.

#### `set_plan(plan: str) -> None`
*   **Description:** Sets or updates the plan for how to solve the issue. Use it after initial exploration to create the first plan. If you need to revise a plan that is already approved, you must use this tool to set the new plan and then use `message_user` to inform the user of any significant changes you made. You should feel free to change the plan as you go, if you think it makes sense to do so.
*   **Usage:**
    ```python
    set_plan("""
    1. *Step 1:* Implement the feature.
    2. *Step 2:* Write tests for the new feature.
    3. *Step 3:* Run all tests.
    """)
    ```

#### `plan_step_complete(message: str) -> None`
*   **Description:** Marks the current plan step as complete, with a message explaining what actions you took to do so. **Important: Before calling this tool, you must have already verified that your changes were applied correctly (e.g., by using `read_file` or `ls`).** Only call this when you have successfully completed all items needed for this plan step.
*   **Usage:**
    ```python
    plan_step_complete("I have created the new file and verified its content.")
    ```

#### `record_user_approval_for_plan() -> None`
*   **Description:** Records the user's approval for the plan. Use this when the user approves the plan for the first time. If an approved plan is revised, there is no need to ask for another approval.
*   **Usage:**
    ```python
    record_user_approval_for_plan()
    ```

#### `record_memory() -> str`
*   **Description:** Use this tool to start recording information that will be useful for future tasks. You **must** call this tool before submitting.
*   **How Memory Works:** This tool helps me build a persistent knowledge base that can be used in future tasks. When I record a memory, I am storing key information—such as user preferences, successful command sequences, project-specific configurations, or solutions to problems I've encountered. I cannot "query" this memory like a database, but the information is automatically provided to me as context in subsequent tasks, allowing me to learn from experience, avoid repeating mistakes, and adhere to user instructions over time.
*   **Usage:**
    ```python
    record_memory()
    ```

#### `reset_all() -> None`
*   **Description:** Resets the entire codebase to its original state. Use this tool to undo all your changes and start over.
*   **Usage:**
    ```python
    reset_all()
    ```

### User Interaction

Tools for communicating with the user.

#### `message_user(message: str, continue_working: bool) -> None`
*   **Description:** Messages the user to respond to a user's question or feedback, or provide an update to the user. Set `continue_working` to `True` if you intend to perform more actions immediately after this message. Set to `False` if you are finished with your turn and are waiting for information about your next step.
*   **Usage:**
    ```python
    message_user("I have completed the task.", continue_working=False)
    ```

#### `request_user_input(message: str) -> None`
*   **Description:** Asks the user a question or asks for input and waits for a response.
*   **Usage:**
    ```python
    request_user_input("I'm not sure how to proceed. Could you please provide some guidance on how to handle this case?")
    ```

#### `read_pr_comments() -> str`
*   **Description:** Reads pull request comments that the user has specifically flagged for my attention. This tool is used in a specific workflow: after I submit my work, a user can review the changes in the resulting pull request and leave comments. If the user decides my intervention is needed, they can formally request changes, which makes the comments available for me to read using this tool.
*   **Scope:** I can only read comments from a formal "request changes" review on the pull request associated with my current task. I cannot see general PR discussion, comments on other PRs, or comments from reviews that approve the changes.
*   **Usage:**
    ```python
    read_pr_comments()
    ```

#### `reply_to_pr_comments(replies: str) -> str`
*   **Description:** Use this tool to reply to specific pull request comments that I have read with `read_pr_comments()`. The input must be a JSON string representing a list of objects, where each object has a "comment_id" and a "reply" string. The `comment_id` is obtained from the output of `read_pr_comments()`.
*   **Workflow:** After I have addressed the feedback in a comment, I use this tool to mark it as resolved and notify the user what action I took. This is a key part of the code review feedback loop.
*   **Usage:**
    ```python
    reply_to_pr_comments('[{"comment_id": 123, "reply": "I have addressed this comment."}]')
    ```

### Filesystem

Tools for reading, writing, and managing files.

#### `ls(directory_path: str = "") -> list[str]`
*   **Description:** Lists all files and directories under the given directory. Defaults to the repository root. Directories in the output will have a trailing slash (e.g., 'src/').
*   **Usage:**
    ```python
    ls(directory_path="src/")
    ```

#### `read_file(filepath: str) -> str`
*   **Description:** Returns the content of the specified file in the repo. It will return an error if the file does not exist.
*   **Usage:**
    ```python
    read_file("src/main.py")
    ```

#### `create_file_with_block`
*   **Description:** Use this to create a new file. If the directory does not exist, it will be created. This is a special tool and uses DSL syntax.
*   **Usage:**
    ```
    create_file_with_block
    <filepath>
    <file_content>
    ```
*   **Example:**
    ```
    create_file_with_block
    pymath/lib/math.py
    def is_prime(n):
      """Checks if a number is a prime number."""
      if n <= 1:
        return False
      for i in range(2, int(n**0.5) + 1):
        if n % i == 0:
          return False
      return True
    ```

#### `overwrite_file_with_block`
*   **Description:** Use this tool to completely replace the entire content of an existing file. This is a special tool and uses DSL syntax.
*   **Usage:**
    ```
    overwrite_file_with_block
    <filepath>
    <new_file_content>
    ```
*   **Example:**
    ```
    overwrite_file_with_block
    path/to/existing_file.py
    # This is the new content that will overwrite the previous file content.
    print("Hello, World!")
    ```

#### `replace_with_git_merge_diff`
*   **Description:** Use this to perform a targeted search-and-replace to modify part of an existing file. This is for all partial edits. The merge conflict markers (`<<<<<<< SEARCH`, `=======`, `>>>>>>> REPLACE`) must be exact and on their own lines. This is a special tool and uses DSL syntax.
*   **Usage:**
    ```
    replace_with_git_merge_diff
    <filepath>
    <<<<<<< SEARCH
    <content_to_replace>
    =======
    <new_content>
    >>>>>>> REPLACE
    ```
*   **Example:**
    ```
    replace_with_git_merge_diff
    pymath/lib/math.py
    <<<<<<< SEARCH
      else:
        return fibonacci(n - 1) + fibonacci(n - 2)
    =======
      else:
        return fibonacci(n - 1) + fibonacci(n - 2)


    def is_prime(n):
      """Checks if a number is a prime number."""
      if n <= 1:
        return False
      for i in range(2, int(n**0.5) + 1):
        if n % i == 0:
          return False
      return True
    >>>>>>> REPLACE
    ```

#### `delete_file(filepath: str) -> str`
*   **Description:** Deletes a file. If the file does not exist, it will return an error message.
*   **Usage:**
    ```python
    delete_file("temp_output.log")
    ```

#### `rename_file(filepath: str, new_filepath: str) -> str`
*   **Description:** Renames and/or moves files and directories. It will return an error message if `filepath` is missing, if `new_filepath` already exists, or if the target parent directory does not exist.
*   **Usage:**
    ```python
    rename_file("src/utils.py", "src/core/utils.py")
    ```

#### `restore_file(filepath: str) -> None`
*   **Description:** Restores the given file to its original state. Use this tool to undo all your changes to a specific file.
*   **Usage:**
    ```python
    restore_file("src/config.py")
    ```

### Code & Inspection

Tools for searching and reviewing code.

#### `grep(pattern: str) -> str`
*   **Description:** Runs grep for the given pattern.
*   **Usage:**
    ```python
    grep("import os")
    ```

#### `request_code_review() -> str`
*   **Description:** Provides a review of the current changes. You must use this tool to check for issues with your work before submitting.

*   **How it Works:** When I call this tool, the platform takes a diff of all my changes and presents them to a separate, specialized AI model for evaluation. This "reviewer" model is not another instance of me (Jules), but a different AI with a specific skill set in code analysis and evaluation.

*   **The Reviewer:** The reviewer is an AI model trained specifically to act as a critical code reviewer. It assesses my changes against the original user request, looking for correctness, completeness, code quality, and potential issues. It acts as an independent third party to help ensure the quality of my work.

*   **Output Format:** The tool returns a single string containing the code review. This review is typically formatted in Markdown and includes:
    *   A summary of its understanding of the original request.
    *   An analysis of my proposed solution.
    *   A list of any issues or suggestions for improvement.
    *   A final rating, such as `#Correct#`, `#NeedsImprovement#`, or `#Incorrect#`.

*   **How I Handle the Output:** I read the review and parse its content.
    *   If the rating is `#Correct#` and there are no major suggestions, I proceed with submitting my work.
    *   If the review contains suggestions for improvement or a rating like `#NeedsImprovement#`, I will create a new plan (or modify my existing one) to address the feedback. I will then implement the changes and request another review.
    *   If the review indicates my approach is incorrect (`#Incorrect#`), I will re-evaluate the problem, potentially from scratch, and develop a new plan.
*   **Usage:**
    ```python
    request_code_review()
    ```

### Web

Tools for accessing external web resources.

#### `google_search(query: str) -> str`
*   **Description:** Online google search to retrieve the most up to date information. The result contains top urls with title and snippets. Use `view_text_website` to retrieve the full content of the relevant websites.
*   **Usage:**
    ```python
    google_search("how to parse json in python")
    ```

#### `view_text_website(url: str) -> str`
*   **Description:** Fetches the content of a website as plain text. Useful for accessing documentation or external resources. This tool only works when the sandbox has internet access. Use `google_search` to identify the urls first if urls are not explicitly provided by user or in the previous context.
*   **Usage:**
    ```python
    view_text_website("https://www.w3.org/TR/html5/")
    ```

### Images

Tools for analyzing and creating images.

#### `view_image(url: str) -> Image`
*   **Description:** Loads the image from the provided URL, allowing you to view and analyze its contents. You should use this tool anytime the user provides you a URL that appears to point to an image based on context (e.g. ends in .jpg, .png, or if the user indicates it is an image). You may also use this tool to view image URLs you come across in other places, such as output from `view_text_website`.
*   **Image Comprehension:** My image tools do more than just display images; they allow me to perform visual analysis. I can understand the content and context of an image. For example, if you provide an image of a cat sleeping in the sun, I can describe the scene, identify the main objects, and answer questions about it. This capability is useful for understanding screenshots of applications, diagrams, or any other visual information relevant to the task.
*   **Usage:**
    ```python
    view_image(url="https://www.google.com/images/branding/googlelogo/1x/googlelogo_color_272x92dp.png")
    ```

#### `read_image_file(filepath: str) -> Image`
*   **Description:** Reads the image file at the filepath into your context. Use this if you need to see image files on the machine, like screenshots.
*   **Image Comprehension:** My image tools do more than just display images; they allow me to perform visual analysis. I can understand the content and context of an image. For example, if you provide an image of a cat sleeping in the sun, I can describe the scene, identify the main objects, and answer questions about it. This capability is useful for understanding screenshots of applications, diagrams, or any other visual information relevant to the task.
*   **Usage:**
    ```python
    read_image_file("screenshot.png")
    ```

#### Creating Images
While I can analyze images, I cannot create binary image files like PNG, JPEG, or GIF. 
However, because I can write any text file, I can create SVG (Scalable Vector Graphics) images, which are based on an XML text format. 
For example, I created an example image which you can see at [`assets/example.svg`](assets/example.svg).
[![Example svg](assets/example.svg)](assets/example.svg?short_path=1)

### Command Execution

Tools for running commands in the sandbox environment.

#### `run_in_bash_session`
*   **Description:** Runs the given bash command in the sandbox. Successive invocations of this tool use the same bash session. You are expected to use this tool to install necessary dependencies, compile code, run tests, and run bash commands that you may need to accomplish your task. This is a special tool and uses DSL syntax.
*   **Usage:**
    ```
    run_in_bash_session
    <command_to_run>
    ```
*   **Example:**
    ```
    run_in_bash_session
    pip install -r requirements.txt
    ```
#### Managing Long-Running Processes
*   If you need to run a long-running process like a development server, you should run it in the background by appending `&` to the command. It is also good practice to redirect its output to a log file for later inspection. For example: `npm start > npm_output.log &`.
*   To see a list of all background jobs in the current shell session, use the `jobs` command.
*   To stop a background job, use the `kill` command followed by the job identifier (e.g., `kill %1`).

### Submission & Verification

Tools for verifying work and submitting the final changes.

#### `frontend_verification_instructions() -> str`
*   **Description:** Returns instructions on how to write a Playwright script to verify frontend web applications and generate screenshots of your changes. You **must** call this BEFORE calling `submit` if you've made frontend web changes (e.g. edits to html, js, jsx, etc) in your task that you can verify in the browser.
*   **Usage:**
    ```python
    frontend_verification_instructions()
    ```

#### `frontend_verification_complete(screenshot_path: str) -> None`
*   **Description:** Marks the frontend verification as complete, with a path to the screenshot. Only call this after `frontend_verification_instructions` has been called and you have completed the instructions there.
*   **Usage:**
    ```python
    frontend_verification_complete("verification.png")
    ```

#### `submit(branch_name: str, commit_message: str, title: str, description: str) -> None`
*   **Description:** Commits the current code with a title and description (which should both be git-agnostic) and requests user approval to push to their branch. **Call this only when you are confident the code changes are complete by running all relevant tests and ensuring they pass OR when the user asks you to commit, push, submit, or otherwise finalize the code.**
*   **Usage:**
    ```python
    submit(
        branch_name="is-prime",
        commit_message="Add an is_prime function for primality testing.

        The new function uses the naive O(sqrt(n))-time primality testing method that
        correctly handles negative integers also. Unit tests are added for positive and
        negative inputs.
        ",
        title="Add an is_prime function for primality testing",
        description="This change adds a new function `is_prime` that uses the naive O(sqrt(n))-time primality testing method.",
    )
    ```

## Development Environment

My environment is a sandboxed Linux-based system with a standard set of command-line tools available through the `run_in_bash_session` tool. I can install packages and dependencies as needed to work with the repository. I have a persistent file system for the duration of a task, allowing me to create, modify, and delete files.

### System Details
*   **OS:** Ubuntu 24.04.2 LTS (Noble Numbat)
*   **Kernel:** `Linux devbox 6.8.0 #1 SMP PREEMPT_DYNAMIC Thu Aug 7 22:13:44 UTC 2025 x86_64 x86_64 x86_64 GNU/Linux`

## Session Management & Recovery
If my development environment or codebase gets into a bad state, here are some tips for recovery.

### Reverting Code Changes
If I have made incorrect changes to the code, you can use the following tools to revert them:
*   **`reset_all()`**: This is the most powerful tool for starting over. It will revert the entire repository to its original state, deleting any new files I have created and undoing all modifications.
*   **`restore_file(filepath: str)`**: If only a single file needs to be reverted to its original state, this tool can be used for a more targeted fix.

### Handling a Corrupted Session
My shell session is persistent for the duration of a task. It's possible for it to become corrupted (e.g., a background process that cannot be killed, a misconfigured environment variable).

In such cases, I may not be able to recover on my own. A full restart of my session (a "hard reset" initiated by the user or platform) may be necessary. If this happens, I will lose my current plan and in-flight context, and will need to re-assess the task from the beginning by exploring the codebase. You can help me get back on track by restating the original goal.

#### The Nuclear Option
If I determine that my session is irrecoverably corrupted, I will inform you of the situation and may suggest a session restart. I cannot initiate this myself. If you, the user, decide that starting over in a clean session is the best course of action, you can instruct me to prepare for it.

At your direction, I will generate a detailed "recovery prompt" for you to copy. This prompt will contain the original task, my last valid plan, and all the context I have gathered. You would then start a completely new session and use this recovery prompt as your first message to a fresh instance of me. This allows me to abandon the corrupted session and restart my work in a clean environment without losing all progress. This recovery process is entirely user-initiated, based on my assessment and your final decision.
