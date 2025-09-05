# Attogram Agents

`AGENTS` files for your AI.

`HUMANS` files for you.

Standardize your AI collaboration process.

## For AI assistants
- [./AGENTS.md](./AGENTS.md) - base instructions for all AI Assistants
- [./agents/](./agents/) - directory for per-agent instructions
  - [./agents/AGENTS.jules.md](./agents/AGENTS.jules.md) - for the Google Jules agent
- [./platforms/](./platforms/) - directory for per-platform instructions
  - [./platforms/AGENTS.bash.md](./platforms/AGENTS.bash.md) - for Bash
  - [./platforms/AGENTS.php.md](./platforms/AGENTS.php.md) - for PHP
  - [./platforms/AGENTS.php.laravel.md](./platforms/AGENTS.php.laravel.md) - for PHP on Laravel
  
## For Humans
- [./HUMANS.md](./HUMANS.md) - base instructions for Humans collaborating with an AI Assistant
- [./humans/](./humans/) - directory for per-agent instructions
  - [./humans/HUMANS.jules.md](./humans/HUMANS.jules.md) - for working with the Google Jules agent

## Why `AGENTS.md` and `HUMANS.md`?

Standard files like `README.md` and `CONTRIBUTING.md` are for general project information and contribution guidelines.

This project uses a special workflow involving AI assistants, which requires more specific instructions for both the AI and the human collaborators.

-   **`AGENTS.md`** files contain specific, machine-readable instructions for the AI assistants. They define the AI's goals, technical standards, and workflow.
-   **`HUMANS.md`** files contain guidance for human developers on how to best collaborate with the AI assistants.

This separation ensures that the right instructions are given to the right audience, making the collaboration between humans and AI more effective.

## Development

We welcome contributions!

- [`./.repo/`](./.repo/) - internal instructions for agents working on this repository

## License

This project is dedicated to the public domain under the [CC0 1.0 Universal](LICENSE) license.

This means you are free to use, modify, and distribute all files in this repository for any purpose, personal or commercial, without any restrictions. You can copy any file you want, or all of them. You can change them however you like.

Attribution is not required, but it is always appreciated! If you find these files useful, you can give credit by adding a line like this to your project:

> AGENTS/HUMANS files based on the [attogram/agents](https://github.com/attogram/agents) project.
