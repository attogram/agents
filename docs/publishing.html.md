[base](../README.md) > [docs](./README.md) > [publishing](./publishing.md) > Advanced Publishing with HTML

# Advanced Publishing: HTML, Previews, and More

This guide covers the more advanced features of the publishing platform,
including using HTML, previewing your site locally, and understanding the
platform's limitations.

## Using HTML for More Control

While Markdown is easy to use, you can also use standard HTML (`.html`) files
for your pages.
This is useful for complex layouts that require specific HTML structures or
CSS classes.

You can create new `.html` files or add existing ones to the repository, and
they will be published as pages on your site.

While most HTML tags are stripped for security, GitHub Pages allows a
"whitelist" of safe tags for advanced formatting.

A great example is creating a collapsible section using `<details>` and
`<summary>`.

```html
<details>
  <summary>Click here to see the details!</summary>

  This content is hidden until you click the summary. You can put any Markdown
  content in here, including lists, code blocks, or images.
</details>
```

Other useful HTML tags that are generally allowed include `<sub>` for
<sub>subscript</sub>, `<sup>` for <sup>superscript</sup>, and `<kbd>` for
styling keyboard inputs like <kbd>Ctrl</kbd>+<kbd>C</kbd>.

## Advanced Theming

### Using Other Themes

You are not limited to the themes supported by default.
Using the `remote_theme` option in `_config.yml`, you can use almost any
public Jekyll theme hosted on GitHub.

```yaml
# remote_theme: owner/repository-name
remote_theme: jekyll/minima
```

### Customizing a Theme's CSS

If you want to add your own custom styles without creating a whole new theme,
you can override the theme's CSS.

1.  Create a file named `/assets/css/style.scss`.
2.  Add the following lines to the top of the file.
    This imports the theme's default stylesheet.

    ```scss
    ---
    ---

    @import "{{ site.theme }}";
    ```

3.  Below the `@import` line, you can add any custom CSS you want.

---

## Understanding the Limitations

GitHub Pages is a powerful tool, but it's important to understand its
limitations.

- **Static Sites Only:** This is the most important limitation.
  GitHub Pages cannot run server-side code (like PHP, Python, or a
  database).
  It can only serve static files: HTML, CSS, JavaScript, images, etc.
  This means you cannot have features like a user login system, a shopping
  cart, or a server-side contact form.

- **Usage Limits:** For repositories on the free plan, GitHub Pages has some
  soft limits:
  - **Size:** Your repository should ideally stay under 1GB.
  - **Bandwidth:** Your site has a soft limit of 100GB of bandwidth per
    month.
  - **Builds:** Your site will be rebuilt up to 10 times per hour.
    Pushing many small commits in a short period might cause some builds to be
    skipped.

- **No Custom Jekyll Plugins:** GitHub Pages only supports a specific list of
  Jekyll plugins.
  You cannot use custom or third-party plugins that are not on
  [this list](https://pages.github.com/versions/).

- **Site Visibility:** If your repository is public, your GitHub Pages site
  will be public.
  If your repository is private, your site will also be public unless you have
  a paid GitHub plan (Pro, Team, or Enterprise).

---

## Advanced Topics

### Previewing Your Site Locally

The default workflow is to push changes and wait for GitHub to publish them.
For larger changes, you may want to preview your site on your own computer
before publishing.

This requires installing Ruby and Jekyll.
While the setup can be technical, the benefit is that you can run a local web
server that behaves exactly like GitHub Pages and see your changes instantly
at `http://localhost:4000`.

To learn how to do this, follow the official guide from GitHub:

- **[Testing your GitHub Pages site locally with Jekyll](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/testing-your-github-pages-site-locally-with-jekyll)**

### Creating a Navigation Menu

Many themes allow you to create a persistent navigation menu at the top of
your site.
The implementation details depend on the theme, but it is often configured
in the `_config.yml` file.

For example, the popular "Minima" theme looks for a `header_pages` array in
your `_config.yml`:

```yaml
# In _config.yml
header_pages:
  - about.md
  - contact.md
```

The default `primer` theme does not support this feature out-of-the-box.
To add a navigation menu, you will need to switch to a different theme or add
your own custom HTML layout.

**Always check the documentation for your chosen theme** to see what
navigation features it supports and how to configure them.
