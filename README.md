# sandboxctl-cicd

Reusable GitHub Actions workflows for the [sandboxctl](https://github.com/butler54/sandboxctl) ecosystem.

## Workflows

| Workflow | Trigger | Purpose |
|----------|---------|---------|
| `python-quality.yml` | `workflow_call` | Pre-commit hooks + pytest matrix with Codecov |
| `commitlint.yml` | `workflow_call` | Validate PR titles against conventional commits |
| `python-release.yml` | `workflow_call` | Semantic release → PyPI (OIDC) → Sigstore → GitHub Releases |
| `block-ide-dirs.yml` | `workflow_call` | Reject `.vscode/` and `.claude/` from commits |

## Composite Actions

| Action | Purpose |
|--------|---------|
| `actions/trivy-scan` | Trivy container image vulnerability scan with SARIF output |

## Usage

```yaml
jobs:
  quality:
    uses: butler54/sandboxctl-cicd/.github/workflows/python-quality.yml@main
    with:
      python-versions: '["3.12", "3.13"]'
```

## Security

All workflows include:
- SHA-pinned third-party actions
- `step-security/harden-runner` on every job
- `persist-credentials: false` on checkout
- Minimal permissions per job

## License

Apache-2.0
