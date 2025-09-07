[base](../README.md) > [docs](./README.md) > [publishing](./publishing.md) > Publishing with Magic Links

# Publishing with Magic Links

"Magic Links" are special URLs that can pre-fill a new file in a GitHub
repository with template content.
This is a powerful way to encourage community contributions by making it easy
for users to submit content in a structured format, such as a bug report, a
testimonial, or a new blog post.

## How They Work

The link is a standard URL used to create a new file on GitHub, but it is
enhanced with query parameters to specify a filename and pre-fill its
content.

Here is a generic example of what the Markdown for a magic link might look
like:

```markdown
[<kbd>Click Here to Add a New Item</kbd>](https://github.com/{OWNER}/{REPO}/new/{BRANCH}/?filename={PATH_TO_FILE}&value={URL_ENCODED_CONTENT})
```

### Key Parameters

- `filename`: This specifies the directory and name of the file to be created.
  You can use placeholders to guide users, for example:
  `_posts/YYYY-MM-DD-your-title.md`.
  This encourages good file naming conventions.
- `value`: This contains the URL-encoded content that will pre-fill the new
  file.

## Deconstructing the `value` Parameter

The `value` parameter is the core of the magic link.
It's your template, but URL-encoded.

Here is an example of a decoded template for a simple blog post:

```yaml
---
layout: post
title: "[YOUR TITLE HERE]"
date: YYYY-MM-DD
description: "[A one-sentence summary of your post]"
author: "[Your Name or GitHub Username]"
---

[YOUR FULL CONTENT HERE. Write as much as you want!]

**How to add images:**
1. After creating this file, drag & drop your images into this folder.
2. Link to them with `![Image description](./your-image-name.png)`
```

This example uses a standard Jekyll post format with YAML front matter.
The placeholders guide the user on what to fill in.

## How to Create Your Own Magic Link

1.  **Write Your Template Content:** In a text editor, write the exact
    content you want to pre-fill for the user.
    Use clear placeholders like `[REPLACE THIS]` to indicate where they should
    add their own information.

2.  **URL-Encode the Content:** Your template content must be URL-encoded to
    be safely included in the link.
    This process converts special characters (like spaces, newlines, and
    symbols) into a format that can be transmitted over the internet.
    There are many free online tools available for URL encoding.
    Simply paste your template content into one of these tools to get the
    encoded version.

3.  **Construct the Final URL:** Assemble the link by combining the base URL
    and your parameters.
    - **Base URL:** `https://github.com/{OWNER}/{REPO}/new/{BRANCH}/`
      - Replace `{OWNER}`, `{REPO}`, and `{BRANCH}` with your repository's
        information.
    - **Filename:** `?filename=path/to/your/new-file.md`
      - Define the path and name for the new file.
    - **Value:** `&value={YOUR_ENCODED_CONTENT}`
      - Paste your URL-encoded template content here.

4.  **Create the Markdown Link:** For easy use, embed your final URL into a
    Markdown link.
    Using `<kbd>` tags can make the link appear more like a button, which can
    improve user experience.

    ```markdown
    [<kbd>Click Here to Contribute</kbd>](YOUR_FINAL_URL)
    ```
