[base](../README.md) > [docs](./README.md) > [ai](./ai.md) > Guiding AI with AGENTS.md

# Guiding AI with `AGENTS.md`

The `AGENTS.md` file is a special document within this repository designed to
be a direct line of communication between you (the user) and any AI agent or
assistant working on your project.
Think of it as a set of permanent instructions or a "cheat sheet" for the AI.

## What is its Purpose?

While you can give an AI instructions in a prompt, those instructions are
temporary and specific to that one conversation.
The `AGENTS.md` file provides a persistent set of rules and guidelines that
the AI can refer to at any time.

This is particularly useful for establishing:

- **Coding Standards:** "Always use tabs, not spaces."
- **Architectural Rules:** "All new components must be registered in the main
  application file."
- **Testing Requirements:** "Every new function must be accompanied by a unit
  test."
- **Repository-Specific Information:** "The `api/` directory is
  auto-generated, do not edit it directly."

## How to Use and Modify It

The `AGENTS.md` file is written in simple Markdown.
You can edit it just like any other text file.

### Best Practices

1.  **Be Clear and Direct:** Write instructions as if you are speaking
    directly to the AI.
    Use clear, unambiguous language.
2.  **Use Markdown for Structure:** Use headings, bullet points, and code
    blocks to keep the document organized and easy for the AI to parse.
3.  **Keep It Updated:** As your project evolves, so should your `AGENTS.md`
    file.
    If you change your architecture or coding standards, update the file to
    reflect those changes.
4.  **Reference It in Your Prompts:** For best results, remind the AI to look
    for and follow the instructions in your `AGENTS.md` file as part of your
    initial prompt.
    The `prompting-ai-agents.md` guide provides examples of how to do this.

By maintaining a well-structured `AGENTS.md` file, you can significantly
improve the quality and consistency of the work done by AI agents on your
project, reducing the need for corrections and rework.
