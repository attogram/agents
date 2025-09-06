AGENTS.bash.md v0.0.1

# Bash and BATS Platform Guide

This document provides guidelines for writing and testing Bash scripts in this repository.

Related documents:
- [PHP Platform Guide](./AGENTS.php.md)
- [Laravel Platform Guide](./AGENTS.php.laravel.md)

## 1. Core Scripting Principles

The scripting guidelines are heavily based on the **[Bash Style Guide by Dave Eddy](https://style.ysap.sh)**, which should be considered the primary reference for style.

- **Shebang:** Start scripts with `#!/usr/bin/env bash` for portability.
- **Error Checking:** Always check for potential errors, especially for commands that can fail, like `cd`.

  ```bash
  # wrong
  cd /some/path
  rm file

  # right
  cd /some/path || exit 1
  rm file
  ```

- **`set -e`:** Do not use `set -e`. Handle errors explicitly.
- **Quoting:** Always quote variable expansions (`"$var"`) to prevent word-splitting and globbing issues.
- **Variables:** Use `local` for all variables inside functions.
- **Conditionals:** Always use `[[ ... ]]` for conditional testing.
- **Command Substitution:** Always use `$(...)` for command substitution, not backticks.

For a comprehensive guide, refer to the [Bash Style Guide](https://style.ysap.sh).

## 2. Testing with BATS (Bash Automated Testing System)

This project uses BATS for testing. Tests are located in the `tests/` directory and have a `.bats` extension.

- **Running Tests:**
  - To run all tests, execute `bats tests/`.
  - To run a specific test file, execute `bats tests/my_test.bats`.
- **Test Structure:**

  ```bash
  #!/usr/bin/env bats

  @test "description of the test" {
    run my_script "some argument"
    [ "$status" -eq 0 ]
    [ "$output" = "expected output" ]
  }
  ```

- **Key BATS Variables:** `$status`, `$output`, `$lines`.

For full documentation, see the [BATS project on GitHub](https://github.com/bats-core/bats-core).
