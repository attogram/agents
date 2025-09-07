[base](../README.md) > [docs](./README.md) > [workflows](./workflows.md) > Secrets Management

# Secrets Management in GitHub Actions

Properly managing secrets like API keys, access tokens, and other credentials
is a critical aspect of security.
This guide explains the best practice of using GitHub Actions secrets to handle
sensitive information.

## Why Secret Management is Important

**Never commit secrets directly to your repository.**
Once a secret is in your git history, it should be considered compromised,
even if you later remove it from the current version of the code.
A public repository is visible to everyone, and malicious actors actively
scan for exposed credentials.

Leaked secrets can lead to:

- Unauthorized access to your accounts and services.
- Financial loss (e.g., if an API key for a paid service is stolen).
- Damage to your project's reputation.

## Using GitHub Actions Secrets

GitHub provides a secure way to store and use secrets within your repository
for use in GitHub Actions workflows.

### How it Works

1.  **Encrypted Storage:** Secrets are stored as encrypted values at the
    repository or organization level.
2.  **Limited Access:** Secrets are only exposed to the specific GitHub Actions
    workflows you choose.
    They are not accessible to collaborators or even the repository owner once
    they are set.
3.  **Redacted Logs:** GitHub automatically redacts secrets from workflow logs,
    preventing them from being accidentally exposed in build outputs.

### How to Add a Repository Secret

1.  Navigate to your repository on GitHub.
2.  Go to **Settings** > **Secrets and variables** > **Actions**.
3.  Click the **New repository secret** button.
4.  Enter a name for your secret (e.g., `NPM_TOKEN`, `AWS_ACCESS_KEY_ID`).
    This name will be used to reference the secret in your workflow files.
5.  Paste the secret value into the **Value** field.
6.  Click **Add secret**.

![GitHub new secret page](https://docs.github.com/assets/cb-57155/images/help/repository/actions-secrets-tab.png)

### How to Use a Secret in a Workflow

Once a secret is stored, you can access it in your workflow `.yml` files using
the `secrets` context.

Here's an example of a workflow step that uses a secret to publish a package
to the npm registry:

```yaml
- name: Publish to npm
  uses: actions/setup-node@v3
  with:
    node-version: "18"
    registry-url: "https://registry.npmjs.org"
- run: npm publish
  env:
    NODE_AUTH_TOKEN: ${{ secrets.NPM_TOKEN }}
```

In this example:

- `secrets.NPM_TOKEN` refers to a repository secret named `NPM_TOKEN`.
- The secret's value is assigned to the `NODE_AUTH_TOKEN` environment
  variable, which is used by the `npm publish` command for authentication.

By using GitHub Actions secrets, you can automate workflows that require access
to sensitive information without compromising on security.
It's a fundamental practice for any project that interacts with external
services.
