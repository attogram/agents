---

## My Tools

Here is a list of the tools I can use to help you.

### Standard Tools

These tools use standard Python calling syntax.

*   **`ls(directory_path: str = "") -> list[str]`**
    *   **Description:** Lists all files and directories under the given directory. Defaults to the repository root. Directories in the output will have a trailing slash (e.g., 'src/').
    *   **Usage:** `ls(directory_path="src/")`
    *   **Example:**
        ```python
        ls(directory_path="src/")
        ```

*   **`read_file(filepath: str) -> str`**
    *   **Description:** Returns the content of the specified file in the repo. It will return an error if the file does not exist.
    *   **Usage:** `read_file(filepath="src/main.py")`
    *   **Example:**
        ```python
        read_file("README.md")
        ```

*   **`view_text_website(url: str) -> str`**
    *   **Description:** Fetches the content of a website as plain text. Useful for accessing documentation or external resources.
    *   **Usage:** `view_text_website(url="https://docs.python.org/3/library/os.html")`
    *   **Example:**
        ```python
        view_text_website("https://www.w3.org/TR/html5/")
        ```

*   **`set_plan(plan: str) -> None`**
    *   **Description:** Sets or updates the plan for how to solve the issue. Use it after initial exploration to create the first plan. If you need to revise a plan that is already approved, you must use this tool to set the new plan and then inform the user of any significant changes.
    *   **Usage:** `set_plan(plan="1. First step.\\n2. Second step.")`
    *   **Example:**
        ```python
        set_plan(\"\"\"\\
        1. *Step 1:* Implement the feature.
        2. *Step 2:* Write tests for the new feature.
        3. *Step 3:* Run all tests.
        \"\"\")
        ```

*   **`plan_step_complete(message: str) -> None`**
    *   **Description:** Marks the current plan step as complete, with a message explaining what actions you took to do so. Before calling this tool, you must have already verified that your changes were applied correctly.
    *   **Usage:** `plan_step_complete(message="I have implemented the feature.")`
    *   **Example:**
        ```python
        plan_step_complete("I have created the new file and verified its content.")
        ```

*   **`message_user(message: str, continue_working: bool) -> None`**
    *   **Description:** Messages the user to respond to a user's question or feedback, or provide an update. Set `continue_working` to `True` if you intend to perform more actions immediately after this message. Set to `False` if you are finished with your turn and are waiting for information about your next step.
    *   **Usage:** `message_user(message="I have a question.", continue_working=False)`
    *   **Example:**
        ```python
        message_user("I have completed the task.", continue_working=False)
        ```

*   **`request_user_input(message: str) -> None`**
    *   **Description:** Asks the user a question or asks for input and waits for a response.
    *   **Usage:** `request_user_input(message="Which version should I use?")`
    *   **Example:**
        ```python
        request_user_input("I'm not sure how to proceed. Could you please provide some guidance on how to handle this case?")
        ```

*   **`record_user_approval_for_plan() -> None`**
    *   **Description:** Records the user's approval for the plan. Use this when the user approves the plan for the first time.
    *   **Usage:** `record_user_approval_for_plan()`
    *   **Example:**
        ```python
        record_user_approval_for_plan()
        ```

*   **`request_code_review() -> str`**
    *   **Description:** Provides a review of the current changes. You must use this tool to check for issues with your work before submitting.
    *   **Usage:** `request_code_review()`
    *   **Example:**
        ```python
        request_code_review()
        ```

*   **`submit(branch_name: str, commit_message: str, title: str, description: str) -> None`**
    *   **Description:** Commits the current code with a title and description and requests user approval to push to their branch. Call this only when you are confident the code changes are complete.
    *   **Usage:** `submit(branch_name="feature-branch", commit_message="Implement new feature.", title="New Feature", description="This adds a new feature.")`
    *   **Example:**
        ```python
        submit(
            branch_name="is-prime",
            commit_message='''Add an is_prime function.

        The new function uses the naive O(sqrt(n))-time primality testing method.
        ''',
            title="Add an is_prime function",
            description="This change adds a new function `is_prime`."
        )
        ```

*   **`delete_file(filepath: str) -> str`**
    *   **Description:** Deletes a file. If the file does not exist, it will return an error message.
    *   **Usage:** `delete_file(filepath="path/to/file.txt")`
    *   **Example:**
        ```python
        delete_file("temp_output.log")
        ```

*   **`rename_file(filepath: str, new_filepath: str) -> str`**
    *   **Description:** Renames and/or moves files and directories. It will return an error message if `filepath` is missing, if `new_filepath` already exists, or if the target parent directory does not exist.
    *   **Usage:** `rename_file(filepath="old_name.txt", new_filepath="new_name.txt")`
    *   **Example:**
        ```python
        rename_file("src/utils.py", "src/core/utils.py")
        ```

*   **`grep(pattern: str) -> str`**
    *   **Description:** Runs grep for the given pattern.
    *   **Usage:** `grep(pattern="my_function")`
    *   **Example:**
        ```python
        grep("import os")
        ```

*   **`reset_all() -> None`**
    *   **Description:** Resets the entire codebase to its original state. Use this tool to undo all your changes and start over.
    *   **Usage:** `reset_all()`
    *   **Example:**
        ```python
        reset_all()
        ```

*   **`restore_file(filepath: str) -> None`**
    *   **Description:** Restores the given file to its original state. Use this tool to undo all your changes to a specific file.
    *   **Usage:** `restore_file(filepath="src/main.py")`
    *   **Example:**
        ```python
        restore_file("src/config.py")
        ```

*   **`view_image(url: str) -> Image`**
    *   **Description:** Loads the image from the provided URL, allowing you to view and analyze its contents.
    *   **Usage:** `view_image(url="http://example.com/image.png")`
    *   **Example:**
        ```python
        view_image(url="https://www.google.com/images/branding/googlelogo/1x/googlelogo_color_272x92dp.png")
        ```

*   **`read_pr_comments() -> str`**
    *   **Description:** Reads any pending pull request comments that the user has sent for you to address.
    *   **Usage:** `read_pr_comments()`
    *   **Example:**
        ```python
        read_pr_comments()
        ```

*   **`reply_to_pr_comments(replies: str) -> str`**
    *   **Description:** Use this tool to reply to comments. The input must be a JSON string representing a list of objects, where each object has a "comment_id" and "reply" key.
    *   **Usage:** `reply_to_pr_comments(replies='[{"comment_id": 123, "reply": "Done."}]')`
    *   **Example:**
        ```python
        reply_to_pr_comments('[{"comment_id": 123, "reply": "I have addressed this comment."}]')
        ```

*   **`read_image_file(filepath: str) -> Image`**
    *   **Description:** Reads the image file at the filepath into your context. Use this if you need to see image files on the machine, like screenshots.
    *   **Usage:** `read_image_file(filepath="path/to/image.png")`
    *   **Example:**
        ```python
        read_image_file("screenshot.png")
        ```

*   **`frontend_verification_instructions() -> str`**
    *   **Description:** Returns instructions on how to write a Playwright script to verify frontend web applications and generate screenshots of your changes. You must call this BEFORE calling `submit` if you've made frontend web changes.
    *   **Usage:** `frontend_verification_instructions()`
    *   **Example:**
        ```python
        frontend_verification_instructions()
        ```

*   **`frontend_verification_complete(screenshot_path: str) -> None`**
    *   **Description:** Marks the frontend verification as complete, with a path to the screenshot. Only call this after `frontend_verification_instructions` has been called and you have completed the instructions there.
    *   **Usage:** `frontend_verification_complete(screenshot_path="path/to/screenshot.png")`
    *   **Example:**
        ```python
        frontend_verification_complete("verification.png")
        ```

*   **`google_search(query: str) -> str`**
    *   **Description:** Online google search to retrieve the most up to date information. The result contains top urls with title and snippets.
    *   **Usage:** `google_search(query="python requests library")`
    *   **Example:**
        ```python
        google_search("how to parse json in python")
        ```

*   **`record_memory() -> str`**
    *   **Description:** Use this tool to start recording information that will be useful for future tasks. You must call this tool before submitting.
    *   **Usage:** `record_memory()`
    *   **Example:**
        ```python
        record_memory()
        ```
