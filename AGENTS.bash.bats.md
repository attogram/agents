# AI Assistant Guidelines for Bash Projects

This document provides a detailed guide for writing and testing Bash scripts in this project. The scripting guidelines are heavily based on the **[Bash Style Guide by Dave Eddy](https://style.ysap.sh)**, which should be considered the primary reference for style.

---

## 1. Core Scripting Principles (Credit: Dave Eddy)

When writing Bash scripts, adhere to the following principles to ensure they are safe, predictable, and maintainable.

-   **Shebang:** Start scripts with `#!/usr/bin/env bash` for portability.
-   **Error Checking:** Always check for potential errors, especially for commands that can fail, like `cd`.
    ```bash
    # wrong
    cd /some/path
    rm file

    # right
    cd /some/path || exit 1
    rm file
    ```
-   **`set -e`:** Do not use `set -e`. Handle errors explicitly. It can have unintended consequences.
-   **Quoting:** This is critical.
    -   Use double quotes (`"`) for strings that require variable expansion.
    -   Use single quotes (`'`) for all other literal strings.
    -   **Always quote variable expansions** (`"$var"`) to prevent word-splitting and globbing issues.
-   **Variables:**
    -   Use lowercase variable names (e.g., `my_var`).
    -   Use `local` for all variables inside functions.
-   **Functions:**
    -   Do not use the `function` keyword.
    -   Use `my_func() { ... }` syntax.
-   **Conditionals:**
    -   Always use `[[ ... ]]` for conditional testing, not `[ ... ]` or `test`.
    -   Use `((...))` for arithmetic comparisons (e.g., `((a > b))`).
-   **Command Substitution:**
    -   Always use `$(...)` for command substitution, not backticks.
-   **Arrays:**
    -   Use Bash arrays to manage lists of items instead of space-separated strings.
    -   Iterate over arrays using `for item in "${my_array[@]}"; do ... done`.
-   **Avoid External Commands:**
    -   Use Bash's built-in parameter expansion for string manipulation (e.g., `${var/foo/bar}`).
    -   Use globbing (`*`) to iterate over files, not `ls`.
    -   Avoid `cat` when a command can read a file directly (e.g., `grep "pattern" file`).
-   **`eval`:** Never use `eval`.

---

## 2. Testing with BATS (Bash Automated Testing System)

This project uses BATS for testing. Tests are located in the `tests/` directory and have a `.bats` extension.

-   **Running Tests:**
    -   To run all tests, execute `bats tests/`.
    -   To run a specific test file, execute `bats tests/my_test.bats`.
-   **Test Structure:** A BATS test file is a Bash script with special syntax.
    ```bash
    #!/usr/bin/env bats

    # setup() { ... } # optional: runs before each test
    # teardown() { ... } # optional: runs after each test

    @test "description of the test" {
      # The test code goes here
      run my_script "some argument"
      [ "$status" -eq 0 ]
      [ "$output" = "expected output" ]
    }
    ```
-   **Key BATS Variables:**
    -   `run`: Executes a command and captures its output and status code.
    -   `$status`: The exit status of the command run.
    -   `$output`: The combined stdout and stderr of the command run.
    -   `$lines`: An array containing each line of the output.
-   **Best Practices for BATS:**
    -   **Isolate Tests:** Each `@test` should be independent. Use `setup` and `teardown` functions to prepare and clean up the test environment if needed.
    -   **Be Specific:** Test descriptions should clearly state what is being tested.
    -   **Assert One Thing:** Ideally, each test should assert a single condition or outcome.
    -   **Use Helpers:** For complex setup or repeated assertions, create helper functions within your test files. BATS automatically exports functions that are not named `setup` or `teardown`.

---

## 3. Where to Get Help

-   **Bash Style Guide:** [style.ysap.sh](https://style.ysap.sh)
-   **BATS Documentation:** [BATS on GitHub](https://github.com/bats-core/bats-core)
-   **Bash Reference:** [BashGuide](https://mywiki.wooledge.org/BashGuide)
