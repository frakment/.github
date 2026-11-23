# Frakment GitHub Workflows

This repository hosts reusable GitHub Actions workflows for Frakment repositories.

Reusable workflows do not run in another repository on their own, so each repository must add a small caller workflow that selects the desired reusable workflow and its trigger.

Call reusable workflows using a full commit SHA, for example:

```yaml
jobs:
  scan:
    uses: frakment/.github/.github/workflows/gitleaks-reusable.yml@<commit-sha>
    permissions:
      contents: read
      security-events: write
```

The `ui-ci-reusable.yml` and `ui-release-reusable.yml` workflows are specific to `frakment/ui`.

The `npm-package-ci-reusable.yml` and `npm-package-release-reusable.yml` workflows are for standalone npm package repositories with a root `package.json` and `package-lock.json`.

The security workflows are reusable by other repositories when their source layout and permissions match the workflow requirements.

Branch rulesets remain repository-specific, and required CI checks should only be configured after the repository has selected and run its workflows.
