[base](../README.md) > [docs](./README.md) > [project](./project.md) > Security Best Practices

# Security Best Practices for Maintainers

As an open-source maintainer, you have a responsibility to ensure your
project is secure.
This guide covers some fundamental security practices to protect both your
project and its users.

## 1. Protect Your Accounts

Your personal accounts are the first line of defense.
If a malicious actor gains access to your GitHub account, they can do
significant damage to your projects.

- **Use a Strong, Unique Password:** Use a password manager to generate and
  store strong, unique passwords for every service you use.
- **Enable Two-Factor Authentication (2FA):** 2FA is the single most
  important thing you can do to secure your accounts.
  Enable it on your GitHub account, your email account, and your package
  manager accounts (e.g., npm).

## 2. Manage Dependencies Securely

Modern software projects rely heavily on third-party dependencies.
A vulnerability in one of your dependencies is a vulnerability in your
project.

- **Enable Dependabot:** GitHub's Dependabot automatically scans your
  dependencies for known vulnerabilities and creates pull requests to update
  them to a secure version.
  This is enabled by default in this repository.
- **Review Dependencies:** When adding a new dependency, consider its
  popularity, maintenance status, and whether it has a good security track
  record.
- **Lock Your Dependencies:** Use a lock file (e.g., `package-lock.json`,
  `yarn.lock`) to ensure that you are using the exact same version of each
  dependency in every environment.

## 3. Handle Security Reports Responsibly

You need a clear process for how a security researcher can report a
vulnerability to you privately.

- **Create a `SECURITY.md` file:** This file, located in the `.github`
  directory, should explain how to report a security vulnerability.
  This repository includes a template [`SECURITY.md`](../.github/SECURITY.md)
  to get you started.
- **Use Private Vulnerability Reporting:** GitHub provides a feature for
  privately reporting vulnerabilities.
  This allows you to discuss and fix a vulnerability in a temporary private
  fork before it's announced to the public.
- **Be Responsive:** When you receive a security report, acknowledge it
  promptly.
  Keep the reporter informed of your progress.
- **Disclose Responsibly:** Once you have a fix, you should disclose the
  vulnerability.
  This typically involves:
  - Publishing a security advisory.
  - Releasing a new version with the fix.
  - Requesting a CVE (Common Vulnerabilities and Exposures) identifier.

## 4. Secure Your Workflows

Your CI/CD workflows can be a target for attackers.

- **Be Cautious with Third-Party Actions:** Only use GitHub Actions from
  trusted creators.
  Pin actions to a specific commit SHA rather than a branch name to prevent
  malicious code from being injected.
- **Limit Permissions:** Grant your workflows only the minimum permissions
  they need to do their job.
- **Manage Secrets:** Use [GitHub Actions secrets](./secrets-management.md)
  to store and use credentials.
  Never hardcode them in your workflow files.

Security is an ongoing process, not a one-time checklist.
By adopting these best practices, you can significantly improve the security
posture of your open-source project and build trust with your users.
