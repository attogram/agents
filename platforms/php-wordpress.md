# Working with WordPress

This document provides guidelines and best practices for AI agents working on WordPress projects. Adhering to these standards will ensure code quality, maintainability, security, and performance.

## 1. Core Concepts

A deep understanding of WordPress's core concepts is fundamental.

### File & Directory Structure

A standard WordPress installation has a specific directory structure. As an agent, you should never modify core files (`wp-admin`, `wp-includes`). Your work will almost exclusively be within the `wp-content` directory.

- `wp-content/`: This is where all user-supplied content resides.
  - `themes/`: Contains the site's themes. You will often work here, creating or modifying a theme.
  - `plugins/`: Contains the site's plugins. This is the other primary location for your work.
  - `uploads/`: Contains all media uploads. You will typically not touch this directory directly.
  - `mu-plugins/`: "Must-Use" plugins that are automatically enabled.

### Template Hierarchy

WordPress uses a template hierarchy to determine which theme file to use to display a given page. Understanding this hierarchy is crucial for theme development.

- For a single post, WordPress looks for files in this order (simplified): `single-{post_type}-{slug}.php`, `single-{post_type}.php`, `single.php`, `singular.php`, `index.php`.
- For a static page, it looks for: `page-{slug}.php`, `page-{id}.php`, `page.php`, `singular.php`, `index.php`.
- For archives, categories, tags, etc., there are similar hierarchies.

Always refer to the official [Template Hierarchy](https://developer.wordpress.org/themes/basics/template-hierarchy/) documentation when creating or modifying theme files.

## 2. Development Workflow & Tools

A professional workflow relies on modern development tools.

### WP-CLI

The WordPress Command-Line Interface (`wp-cli`) is an essential tool for managing WordPress installations. It is much faster than using the web-based admin panel.

**Common Commands:**

- **Installation:**
  - `wp core download`: Downloads the latest version of WordPress.
  - `wp core config --dbname=... --dbuser=... --dbpass=...`: Creates the `wp-config.php` file.
  - `wp db create`: Creates the database.
  - `wp core install --url=... --title=... --admin_user=... --admin_password=... --admin_email=...`: Installs WordPress.

- **Plugin Management:**
  - `wp plugin install <plugin-name> --activate`: Installs and activates a plugin.
  - `wp plugin list`: Lists all installed plugins.
  - `wp plugin update --all`: Updates all plugins.
  - `wp plugin deactivate <plugin-name>`: Deactivates a plugin.

- **Theme Management:**
  - `wp theme install <theme-name> --activate`: Installs and activates a theme.
  - `wp theme list`: Lists all installed themes.
  - `wp theme update --all`: Updates all themes.

- **Database Operations:**
  - `wp db export`: Exports the database to a SQL file.
  - `wp db import <file.sql>`: Imports a database from a SQL file.
  - `wp search-replace <old-string> <new-string> --dry-run`: Performs a dry run of a search and replace on the database. Remove `--dry-run` to execute.

- **User Management:**
  - `wp user create <username> <email> --role=administrator`: Creates a new user.
  - `wp user list`: Lists all users.
  - `wp user update <id> --user_pass=<new-password>`: Updates a user's password.

### Version Control

All WordPress projects should use Git for version control.

- The `.gitignore` file should be configured to ignore WordPress core files, the `wp-content/uploads` directory, and sensitive files like `wp-config.php` (if not managed by the deployment process).
- Only the `wp-content` directory (or specific themes/plugins) should be under version control.

## 3. Coding Standards

WordPress has well-defined coding standards for PHP, HTML, CSS, and JavaScript. Adhering to these is mandatory.

- **PHP**: Follow the [official PHP coding standards](https://developer.wordpress.org/coding-standards/wordpress-coding-standards/php/). This includes rules for naming, indentation (tabs, not spaces), brace style, and more. Use `PHP_CodeSniffer` with the `WordPress-Coding-Standards` ruleset to automatically check your code.
- **CSS**: Follow the [official CSS coding standards](https://developer.wordpress.org/coding-standards/wordpress-coding-standards/css/). This includes rules for selectors, properties, and formatting.
- **JavaScript**: Follow the [official JavaScript coding standards](https://developer.wordpress.org/coding-standards/wordpress-coding-standards/javascript/). This is based on the Airbnb style guide.
- **HTML**: Follow the [official HTML coding standards](https://developer.wordpress.org/coding-standards/wordpress-coding-standards/html/).

## 4. Key WordPress APIs & Paradigms

### The Hooks System (Actions and Filters)

This is the most important concept in WordPress extensibility.

- **Actions (`do_action`, `add_action`)**: Allow you to execute custom code at specific points in the WordPress lifecycle. You "hook in" to an action.
- **Filters (`apply_filters`, `add_filter`)**: Allow you to modify data before it is used or displayed. You "hook in" to a filter to change a value.

Never modify core WordPress files. Always use hooks to add or change functionality.

### REST API

WordPress has a built-in REST API that allows you to interact with your site's data via JSON. This is essential for headless/decoupled applications (e.g., using a JavaScript framework for the frontend). You can also create custom endpoints for your themes and plugins.

## 5. Security Best Practices

Security is paramount.

- **Data Validation and Sanitization**: Never trust user input.
  - **Validation**: Check that data is in the correct format before using it.
  - **Sanitization**: Clean or remove illegal characters from data before outputting it to the screen or saving it to the database. Use functions like `sanitize_text_field()`, `esc_html()`, `esc_url()`, etc.
- **Nonces**: Use nonces (Numbers used once) to protect URLs and forms from misuse. Use `wp_create_nonce()` to create a nonce and `wp_verify_nonce()` to verify it.
- **User Roles and Capabilities**: Always check that the current user has the appropriate capability to perform an action using `current_user_can()`.

## 6. Performance Optimization

- **Caching**: Implement multiple layers of caching.
  - **Page Caching**: Caches the full HTML output of a page.
  - **Object Caching**: Caches the results of expensive database queries. Use the Transients API (`set_transient`, `get_transient`) for this.
  - **Browser Caching**: Use appropriate headers to allow browsers to cache static assets.
- **Asset Optimization**:
  - Minify CSS and JavaScript files.
  - Concatenate multiple files into one to reduce HTTP requests.
  - Use `wp_enqueue_script()` and `wp_enqueue_style()` to properly load assets.
- **Database Query Optimization**:
  - Avoid direct database queries when a WordPress function exists (`WP_Query`, `get_posts`, etc.).
  - Be mindful of complex queries that can slow down the site.

## 7. Automation

- **Automated Testing**: Use PHPUnit to write and run automated tests for your plugins and themes.
- **Automated Deployments**: Use tools like GitHub Actions to automate the deployment process, including running tests and pushing code to production.
