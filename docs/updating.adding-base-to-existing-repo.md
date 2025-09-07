[base](../README.md) > [docs](./README.md) > [updating](./updating.md) > Adding base to an Existing Repo

# Merging `base` Into an Existing Repository

This guide explains how to merge the `attogram/base` repository into your
existing project.
This is useful for incorporating the `base` features, such as the Docker
environment and GitHub Actions, into a project that has already been started.

There are two ways to do this: an easy method using the GitHub web interface,
and an advanced method using the command line on your local machine.

---

## Initial Merge

This section explains how to perform the first merge of `base` into your
repository.

### Easy Method: Using GitHub Codespaces (Web-Based)

This method is recommended if you are not familiar with the command line or do
not have Git installed on your machine.
It uses GitHub Codespaces, which provides a development environment that runs
in your browser.

1.  **Navigate to Your Repository:**
    Go to the main page of your own existing repository on GitHub.

2.  **Launch a New Codespace:**
    - Click the "**<> Code**" button.
    - Go to the "**Codespaces**" tab.
    - Click "**Create codespace on [your-branch-name]**".
      This will create a new development environment and open it in a new browser
      tab.

3.  **Open the Terminal:**
    Once the Codespace has loaded, you will see a code editor and a file
    browser.
    You need to open the terminal:
    - Click the "hamburger" menu (☰) in the top-left corner.
    - Go to "**Terminal**" > "**New Terminal**".

4.  **Run the Merge Commands:**
    In the terminal, you will now run a series of Git commands.
    These are the same commands as the advanced method, but you are running them
    in the browser instead of on your local machine.
    - **Add `base` as a remote:** This tells Git where to find the
      `attogram/base` repository.
      ```bash
      git remote add base https://github.com/attogram/base.git
      ```
    - **Fetch and merge `base`:** This downloads the `base` repository and
      merges it into your project.
      ```bash
      git fetch base
      git merge base/main --allow-unrelated-histories
      ```

5.  **Handle Merge Conflicts:**
    If there are any merge conflicts, the Codespace will highlight the affected
    files in the file browser.
    - Click on a conflicted file to open it.
    - The editor will show you the conflicting changes with markers (`<<<<<<<`,
      `=======`, `>>>>>>>`).
    - You can use the buttons provided by the editor ("**Accept Current
      Change**", "**Accept Incoming Change**", etc.) to resolve the conflicts.
    - Once you have resolved the conflicts in a file, save it.

6.  **Commit and Push the Changes:**
    - Go to the "**Source Control**" tab on the left-hand side (it looks like a
      branching icon).
    - Enter a commit message (e.g., "Merge attogram/base").
    - Click the checkmark icon to commit the changes.
    - Click the "**Sync Changes**" button to push the changes to your
      repository on GitHub.

7.  **Create a Pull Request:**
    - Go back to your repository's main page on GitHub.
    - You will see a notification to create a Pull Request from your recently
      pushed changes.
    - Click on it, review the details, and create the PR.

### Advanced Method: Using the Command Line

This method is for users who are comfortable with the command line and have Git
installed on their local machine.

1.  **Add `base` as a Remote:**
    First, you need to add the `base` repository as a remote to your local Git
    repository.
    This allows you to fetch its branches and history.

    ```bash
    git remote add base https://github.com/attogram/base.git
    ```

2.  **Fetch and Merge `base`:**
    Next, fetch the `base` repository's history and merge its `main` branch
    into your project's main branch.

    ```bash
    git fetch base
    git merge base/main --allow-unrelated-histories
    ```

3.  **Handle Merge Conflicts:**
    It is highly likely that you will encounter merge conflicts.
    To resolve them:
    - Run `git status` to see a list of files with conflicts.
    - Open each conflicting file in your code editor and resolve the conflicts.
    - Stage the resolved files using `git add .`.
    - Commit the merge with `git commit`.

4.  **Create a Pull Request:**
    After the merge is complete, push the changes to your repository and create
    a Pull Request.

---

## Keeping Your Repository Updated

After the initial merge, you can pull in future updates from `base` by running
the following commands:

```bash
git fetch base
git merge base/main
```

You may need to resolve merge conflicts again, just as you did during the
initial merge.

---

## Alternative: Copying Files

If you only want to incorporate a small part of the `base` repository, like a
specific workflow or configuration file, you can simply copy and paste it into
your own project.

For example, you can copy the contents of the
[`.github/`](https://github.com/attogram/base/tree/main/.github) directory to
get the latest GitHub Actions workflows.

This method is simpler than a full merge, but you will need to manually update
the files if you want to get future updates from `base`.
