## 🔄 Reusable CI Workflows

This organization provides reusable GitHub Actions workflows for consistent CI across all repositories.

### Available Workflows

| Workflow | Path | Purpose |
|----------|------|---------|
| PR Title Validation | `.github/workflows/pr-title-reusable.yml` | Enforces Conventional Commits in PR titles |
| Commit Message Lint | `.github/workflows/commitlint-reusable.yml` | Validates all commit messages in a PR |

### How to Use

In any repo, create `.github/workflows/pr-title.yml`:

\`\`\`yaml
name: Validate PR Title
on:
  pull_request:
    types: [opened, edited, synchronize, reopened]
jobs:
  validate:
    uses: <your-org>/.github/.github/workflows/pr-title-reusable.yml@main
\`\`\`

For commitlint, also add `.commitlintrc.json` to your repo root (see [example](./.commitlintrc.json)).

### Allowed Commit Types

`feat`, `fix`, `docs`, `chore`, `ci`, `refactor`, `test`, `perf`, `build`, `revert`