AGENTS.php.md v0.0.1

# PHP Platform Guide

This document provides general guidelines for working on PHP projects in this repository. For framework-specific instructions, please see the corresponding platform guide.

Related documents:

- [Laravel Platform Guide](./AGENTS.php.laravel.md)
- [Bash Platform Guide](./AGENTS.bash.md)

## Testing

- This project uses PHPUnit for testing.
- Run the test suite with the command:
  ```bash
  ./vendor/bin/phpunit
  ```
- All new code must be accompanied by tests.

## Coding Standards

- Adhere to the **PSR-12** coding standard.
- Use a linter or code sniffer to check your code before submitting.
