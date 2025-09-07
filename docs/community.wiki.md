[base](../README.md) > [docs](./README.md) > [community](./community.md) > Using the GitHub Wiki

# Using the GitHub Wiki

The GitHub Wiki is a powerful tool for hosting detailed, long-form documentation
for your project.
Unlike your repository's `README.md` file, which is meant to be a quick
introduction, the wiki provides a dedicated space for comprehensive guides,
tutorials, and reference material.

## `README.md` vs. Wiki: What's the Difference?

Understanding when to use your `README.md` and when to use the wiki is key to
keeping your project's documentation organized and accessible.

- **`README.md`** is the front door to your project.
  It should be concise and provide a high-level overview, installation
  instructions, and a quick start guide.
  It's the first thing most visitors will see.

- **The Wiki** is the library for your project.
  It's the place for "deep dive" content that doesn't fit in the README.
  - **Use for:** In-depth tutorials, API references, design documents, project
    history, and FAQs.
  - **Example:** A detailed guide on "Advanced Configuration Options" or a
    "Contributor's Guide to the Codebase."

By moving detailed documentation to the wiki, you keep your `README.md` clean
and focused, while providing a structured and searchable home for your
project's knowledge base.

## How to Use the Wiki

1.  **Enable the Wiki:** In your repository settings, under the "Features"
    section, check the box for "Wiki."

2.  **Create a Home Page:** Every wiki starts with a `Home.md` page.
    This page should serve as a table of contents, with links to all the other
    pages in your wiki.

3.  **Add and Edit Pages:** You can add new pages and edit existing ones
    directly in the GitHub web interface.
    The wiki uses Markdown, just like the rest of GitHub.

4.  **Link Pages Together:** Create links between your wiki pages to build a
    cohesive and navigable documentation site.
    You can link to another wiki page using the syntax `[[Page Name]]`.

## Best Practices for Maintainers

1.  **Keep it Organized:** Use the `Home.md` page as a table of contents.
    Group related pages together with clear and consistent naming.

2.  **Encourage Contributions:** By default, anyone with push access to your
    repository can edit the wiki.
    Encourage your community to contribute to the documentation.

3.  **Review and Curate:** Periodically review the content of your wiki to
    ensure it is up-to-date and accurate.
    Remove outdated information and refactor pages as your project evolves.

4.  **Link to the Wiki from your `README.md`:** Add a link to your wiki from
    your project's `README.md` file so that visitors can easily find your
    detailed documentation.

By leveraging the GitHub Wiki, you can build a comprehensive and collaborative
documentation site that will help your users and contributors get the most out
of your project.
