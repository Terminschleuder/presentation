# Security policy

## Reporting a vulnerability

Please report privately via GitHub's **private vulnerability reporting**:
Security tab → *Report a vulnerability*. Please do not open a public issue
for a suspected vulnerability.

## Scope

This repo is a Markdown slide deck and its rendering tooling — there is no
runtime code, no secrets, and no deployed artifact beyond the rendered PDF
attached to releases. A security issue here would realistically only involve
CI (e.g. a malicious workflow change), which is covered by branch protection
(required checks, no direct pushes to `main`).

## Dependencies

There are no package manifests; the only third-party tooling is Marp CLI,
which CI runs as a container image. Dependabot covers the Action pins in
[`.github/dependabot.yml`](.github/dependabot.yml).