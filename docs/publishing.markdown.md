[base](../README.md) > [docs](./README.md) > [publishing](./publishing.md) > Publishing with Markdown

# Publishing with Markdown

This repository is pre-configured to act as a simple, powerful, and free
website publishing platform using GitHub Pages.
This guide walks you through how to use it to create and manage your own site.

## Part 1: Choosing Your Website's Design

Your website's look and feel is controlled by a "theme".
This repository uses Jekyll, a static site generator, which has great support
for themes.

### How to Change Your Theme

You can change your website's theme with a single line of code.

1.  Open the `_config.yml` file in the root of your repository.
2.  You will see a line: `theme: jekyll-theme-primer`.
3.  To change the theme, simply replace `jekyll-theme-primer` with the name
    of another supported theme.
    For example: `theme: jekyll-theme-minimal`.
4.  Commit the change, and your site will be rebuilt with the new theme.

### Supported Themes

GitHub Pages officially supports a number of themes.
You can preview them by visiting their repositories.

| Theme Name   | How to Use It (`_config.yml`)      | Preview Link                                                   |
| :----------- | :--------------------------------- | :------------------------------------------------------------- |
| Architect    | `theme: jekyll-theme-architect`    | [View on GitHub](https://github.com/pages-themes/architect)    |
| Cayman       | `theme: jekyll-theme-cayman`       | [View on GitHub](https://github.com/pages-themes/cayman)       |
| Dinky        | `theme: jekyll-theme-dinky`        | [View on GitHub](https://github.com/pages-themes/dinky)        |
| Hacker       | `theme: jekyll-theme-hacker`       | [View on GitHub](https://github.com/pages-themes/hacker)       |
| Leap Day     | `theme: jekyll-theme-leap-day`     | [View on GitHub](https://github.com/pages-themes/leap-day)     |
| Merlot       | `theme: jekyll-theme-merlot`       | [View on GitHub](https://github.com/pages-themes/merlot)       |
| Midnight     | `theme: jekyll-theme-midnight`     | [View on GitHub](https://github.com/pages-themes/midnight)     |
| Minimal      | `theme: jekyll-theme-minimal`      | [View on GitHub](https://github.com/pages-themes/minimal)      |
| Modernist    | `theme: jekyll-theme-modernist`    | [View on GitHub](https://github.com/pages-themes/modernist)    |
| Primer       | `theme: jekyll-theme-primer`       | [View on GitHub](https://github.com/pages-themes/primer)       |
| Slate        | `theme: jekyll-theme-slate`        | [View on GitHub](https://github.com/pages-themes/slate)        |
| Tactile      | `theme: jekyll-theme-tactile`      | [View on GitHub](https://github.com/pages-themes/tactile)      |
| Time Machine | `theme: jekyll-theme-time-machine` | [View on GitHub](https://github.com/pages-themes/time-machine) |

## Part 2: Creating and Editing Content

### The Publishing Workflow

Publishing is as simple as editing text files.

1.  **Edit or Create Files:** Edit an existing Markdown (`.md`) file or
    create a new one.
2.  **Commit and Push:** Save and push your changes to the `main` branch.
3.  **Done!** The website will automatically rebuild and your changes will be
    live in a minute or two.

### Homepage and Other Pages

- **Homepage:** The content of your site's homepage is the `README.md` file
  in the root of the repository.
- **Other Pages:** Any other `.md` file in your repository becomes a page on
  your site.
  For example, `contact.md` will be available at `your-site.com/contact`.

### Organizing Your Site

You can create folders to organize your content.
A file at `docs/about.md` will be available at `your-site.com/docs/about`.

To link between pages, use relative links in your Markdown.
It's best to use paths relative to the current file (e.g., starting with
`./` or `../`).

For example, from your root `README.md`, you could link to a file in `docs`
like this:

```markdown
[Read our About page](./docs/about.md)
```

## Part 3: Advanced Formatting

Markdown is designed to be simple, but it has powerful features for creating
rich content.

### Code Blocks with Syntax Highlighting

````markdown
```javascript
function helloWorld() {
  console.log("Hello, world!");
}
```
````

### Tables

```markdown
| Feature         | Support Level | Notes                               |
| :-------------- | :-----------: | :---------------------------------- |
| Themes          |     Good      | Several supported themes available. |
| Markdown Tables |   Excellent   | Full support for GFM tables.        |
```

### Task Lists

```markdown
- [x] Draft the documentation.
- [ ] Add more examples.
- [ ] Request a review.
```

### Alerts and Blockquotes

```markdown
> [!NOTE]
> This is a note.
> It contains useful information users should know.

> [!WARNING]
> This is a warning.
> It advises about risks or negative outcomes.
```

### Working with Images and Videos

#### Images

The standard Markdown syntax for an image is `![Alt Text](URL)`.

- **Local Images:** `![A diagram of our process](./assets/process-diagram.png)`
- **Remote Images:** `![A photo of the earth from space](https://example.com/path/to/earth.jpg)`

#### Embedding Videos

You can't embed a video player directly, but you can create a clickable
thumbnail that links to the video.
Replace `YOUTUBE_VIDEO_ID_HERE` with your video's ID.

```markdown
[![Watch the video](https://img.youtube.com/vi/YOUTUBE_VIDEO_ID_HERE/0.jpg)](https://www.youtube.com/watch?v=YOUTUBE_VIDEO_ID_HERE)
```

### Page Titles and SEO

To set a custom title and description for a specific page, add a "front
matter" block to the very top of your `.md` file.

```yaml
---
title: About Our Company
description: Learn about our history, our team, and our mission.
image: /assets/our-team-photo.jpg
---
# About Us

This is the rest of your page content...
```

You can also set a site-wide title and description in the `_config.yml` file.
