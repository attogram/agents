[base](../README.md) > [docs](./README.md) > [documentation](./documentation.md) > Documentation Best Practices

# Documentation Best Practices

Good documentation is one of the most important aspects of a successful
software project.
It empowers users, reduces the support burden on maintainers, and encourages
contributions.
This guide covers the art of writing clear and effective documentation.

## The Two Types of Documentation

It's helpful to think of documentation in two main categories: user guides
and reference material.
A good project has both.

### 1. User Guides (Tutorials)

- **Purpose:** To teach a user how to accomplish a specific task.
  They are action-oriented.
- **Audience:** New users or users trying to solve a particular problem.
- **Format:** A step-by-step walkthrough.
  They tell a story.
- **Example:** A guide on "How to deploy this application to a server" or "How
  to build your first plugin."

User guides are like a teacher showing a student how to do something.
They should be easy to follow and focused on a practical outcome.

### 2. Reference Material (The Dictionary)

- **Purpose:** To provide a comprehensive, factual description of the system.
  It is information-oriented.
- **Audience:** Users who already have some familiarity with the project and
  need specific, detailed information.
- **Format:** Organized by topic, like a dictionary or an encyclopedia.
- **Example:** A complete list of all available API endpoints and their
  parameters, or a detailed description of every configuration option in a
  file.

Reference material is like a technical manual.
It should be accurate, exhaustive, and well-organized so that users can
quickly find the exact information they need.

## The Importance of Good Examples

Code examples are the heart of good documentation.
They bridge the gap between theory and practice.

- **Make them practical:** Examples should demonstrate a real-world use case,
  not just the syntax of a function.
- **Make them copy-pasteable:** Ensure that examples can be copied and run
  directly without modification.
  This means including any necessary setup or import statements.
- **Keep them up-to-date:** There's nothing more frustrating than
  documentation with outdated examples.
  As your code evolves, make sure your examples do too.

## Tips for Writing Good Docs

1.  **Know Your Audience:** Write for your users, not for yourself.
    Avoid jargon where possible, or explain it if it's necessary.
2.  **Be Concise:** Get to the point.
    Users are often looking for a quick solution to a problem.
3.  **Use a Clear Structure:** Use headings, lists, and code blocks to make
    your documentation easy to scan.
4.  **Add Visuals:** Screenshots, diagrams, and GIFs can often explain a
    concept more effectively than text alone.
5.  **Document the "Why":** Don't just explain _what_ something does; explain
    _why_ a user might want to use it.
    Provide context.
6.  **Treat Docs like Code:** Documentation should be part of your
    development process.
    When you add a new feature or make a change, update the docs at the same
    time.
    Include documentation in your code review process.

Writing documentation is a continuous process of refinement.
By investing in clear, comprehensive, and user-focused documentation, you are
investing in the long-term success of your project.
