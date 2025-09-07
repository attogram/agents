[base](../README.md) > [docs](./README.md) > [ai](./ai.md) > Prompting AI Agents

# Prompting AI Agents for `attogram/base` Projects

When using AI agents to create or update a repository based on
`attogram/base`, providing a clear, upfront context is the most effective way
to get the results you want.
This guide provides two distinct prompt examples to help you steer AI agents in
the right direction, whether you want to build upon the `base` philosophy or
intentionally modify it.

---

## Prompt 1: Using `base` As-Is

This prompt is ideal when you want to create a new project that adheres to the
core, language-agnostic philosophy of the `attogram/base` template.

### Example Prompt: Create a Personal Blog

```
This project builds upon the attogram/base template.
Please integrate the new website content without removing the core base
repository files or structure.

The main homepage for the site is `README.md`, and all new content should be
linked from there.
You can create new directories for your content as needed, but please do not
modify the core `base` files and directories (such as `.github`, `docs`,
`docker`, etc.).

Please use the existing Jekyll setup for the site, which builds from the root
directory.
Do not install other static site generators like Eleventy.

Finally, please look for and follow any instructions in an `AGENTS.md` file,
as it may contain project-specific guidelines for AI agents.
```

---

## Prompt 2: Modifying `base` for a New Technology

This prompt is for when you want to use `attogram/base` as a starting point
but intend to introduce a specific programming language or framework.
This example uses PHP and Laravel.

### Example Prompt: Add a Laravel Backend

```
This project will use `attogram/base` as a foundation, but we will be
modifying it to support a PHP/Laravel application.

Here are the requirements:
1.  **Add PHP and Laravel:** Please modify the Docker environment to include
    PHP and the necessary extensions for a Laravel application.
2.  **Install Laravel:** Once the environment is updated, install a fresh copy
    of the Laravel framework in a `/src` directory at the repository root.
3.  **Update NGINX:** Configure the NGINX server to point to the `public`
    directory of the Laravel application.
4.  **Preserve Core Files:** Do not remove the existing GitHub Actions
    workflows or the documentation in the `/docs` directory.
    The goal is to integrate Laravel into the `base` template, not replace it.
5.  **Check for `AGENTS.md`:** Please look for and follow any instructions in
    an `AGENTS.md` file, as it may contain project-specific guidelines for AI
    agents.
```

---

## Why These Prompts Work

Providing a detailed, upfront prompt like the examples above is crucial for
several reasons:

- **Sets Clear Expectations:** The AI immediately understands the scope of the
  project.
  It knows whether to preserve the `base` philosophy or to modify it, which is
  the most critical distinction.
- **Reduces Errors and Rework:** By specifying the technology stack (or lack
  thereof) and the desired file structure, you prevent the AI from making
  incorrect assumptions that would need to be corrected later.
- **Empowers the AI:** A clear prompt gives the AI the constraints it needs to
  be creative and effective.
  It can focus on the "how" because you've already defined the "what" and
  "why."
- **Faster, Better Results:** Ultimately, a few minutes spent crafting a
  detailed prompt will save you hours of back-and-forth, leading to a better
  final product that meets your requirements from the start.
