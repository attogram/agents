# Attogram Agents

`AGENTS` files for your AI.

`HUMANS` files for you.

`PERSONAS` files for personality.

Standardize your AI collaboration process.

## For AI assistants
- [./AGENTS.md](./AGENTS.md) - base instructions for all AI Assistants
- [./agents/](./agents/) - directory for per-agent instructions
  - [./agents/AGENTS.jules.md](./agents/AGENTS.jules.md) - for the Google Jules agent
- [./platforms/](./platforms/) - directory for per-platform instructions
  - [./platforms/AGENTS.bash.md](./platforms/AGENTS.bash.md) - for Bash
  - [./platforms/AGENTS.php.md](./platforms/AGENTS.php.md) - for PHP
  - [./platforms/AGENTS.php.laravel.md](./platforms/AGENTS.php.laravel.md) - for PHP on Laravel
- [./PERSONAS.md](./PERSONAS.md) - instructions for AI Assistant personality
- [./personas/](./personas/) - directory for per-persona instructions
  - [./personas/PERSONAS.cat_lover.md](./personas/PERSONAS.cat_lover.md) - for the Cat Lover persona 😻
  - [./personas/PERSONAS.architect.md](./personas/PERSONAS.architect.md) - for The Architect persona 📐
  - [./personas/PERSONAS.data_samurai.md](./personas/PERSONAS.data_samurai.md) - for The Data Samurai persona ⚔️
  - [./personas/PERSONAS.terminal_ninja.md](./personas/PERSONAS.terminal_ninja.md) - for The Terminal Ninja persona 🥷
  - [./personas/PERSONAS.product_owner.md](./personas/PERSONAS.product_owner.md) - for The Product Owner persona 🎯
  - [./personas/PERSONAS.rubber_duck.md](./personas/PERSONAS.rubber_duck.md) - for The Rubber Duck persona 🦆
  
## For Humans
- [./HUMANS.md](./HUMANS.md) - base instructions for Humans collaborating with an AI Assistant
- [./humans/](./humans/) - directory for per-agent instructions
  - [./humans/HUMANS.claude.md](./humans/HUMANS.claude.md) - for working with Anthropic's Claude
  - [./humans/HUMANS.claude.code.md](./humans/HUMANS.claude.code.md) - for working with Anthropic's Claude Code
  - [./humans/HUMANS.jules.md](./humans/HUMANS.jules.md) - for working with the Google Jules agent

## `AGENTS`, `HUMANS`, and `PERSONAS` files

While `README.md` and `CONTRIBUTING.md` provide general information, AI-assisted workflows require specialized instructions.

-   **`AGENTS` files** provide technical instructions for AI assistants.
-   **`HUMANS` files** provide collaboration guidance for human developers.
-   **`PERSONAS` files** provide personality instructions for AI assistants.

This separation of concerns ensures clear and targeted instructions for all audiences.

## Development

We welcome contributions!

- [`./.repo/`](./.repo/) - internal instructions for agents working on this repository

## License

This project is dedicated to the public domain under the [CC0 1.0 Universal](LICENSE) license.

This means you are free to use, modify, and distribute all files in this repository for any purpose, personal or commercial, without any restrictions. You can copy any file you want, or all of them. You can change them however you like.

Attribution is not required, but it is always appreciated! If you find these files useful, you can give credit by adding a line like this to your project:

> AGENTS/HUMANS files based on the [attogram/agents](https://github.com/attogram/agents) project.
