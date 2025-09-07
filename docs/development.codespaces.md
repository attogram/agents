[base](../README.md) > [docs](./README.md) > [development](./development.md) > GitHub Codespaces

# GitHub Codespaces

This repository is configured to use
[GitHub Codespaces](https://github.com/features/codespaces) to provide a
complete, cloud-based development environment.

## How It Works

The configuration is defined in the
[`.devcontainer/devcontainer.json`](../.devcontainer/devcontainer.json) file.
This file instructs GitHub Codespaces to:

1.  **Use the Docker Environment:** It references our
    [`docker-compose.yml`](../docker-compose.yml) file to spin up the same
    development environment that you would use locally.
2.  **Install VS Code Extensions:** It automatically installs a few
    recommended Visual Studio Code extensions (Docker and GitLens) to enhance
    the development experience.

## Getting Started

To get started with Codespaces:

1.  Click the **"Code"** button at the top of the repository page.
2.  Select the **"Codespaces"** tab.
3.  Click **"Create codespace on main"**.

GitHub will prepare your cloud environment, and you will be taken to a
web-based version of VS Code, fully configured and ready to go.
The terminal within VS Code will be inside the running development container.

## How to Serve the "pong" Page on Port 80 in a New GitHub Codespace

1. **Open a Codespace:**
   - Go to your repository on GitHub.
   - Click the **Code** button, select the **Codespaces** tab, and create a
     new Codespace.

2. **Start NGINX in the Dev Container:**
   - Open the integrated terminal in VS Code.
   - Run:
     ```bash
     service nginx start
     ```

3. **Manually Forward Port 80:**
   - Open the **PORTS** tab (bottom panel, tiny icon).
   - Click the **Forward a Port** button (`+` icon).
   - Enter `80` as the port number and confirm.
   - The url to your codespace instance will now appear in the 'Forwarded
     Ports' column

4. **Open the "pong" Page:**
   - Copy the forwarded URL shown in the PORTS tab (it will look like
     `https://<codespace-name>-80.app.github.dev/`).
   - Open it in your browser:
     ```bash
     "$BROWSER" https://<codespace-name>-80.app.github.dev/
     ```

You should now see the word **pong**
