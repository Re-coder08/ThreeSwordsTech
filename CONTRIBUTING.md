# Git Flow Workflow

This project uses **Git Flow** for deployment and release management. All development follows this strict branching strategy.

## Branch Structure

- **`main`** — Production-ready code. Every commit here represents a stable release.
  - Protected: PR reviews required before merging
  - Only receives merges from release and hotfix branches

- **`develop`** — Integration branch for features and fixes. This is the base branch for all development.
  - Protected: PR reviews required before merging
  - Deploys to staging/preview environment

- **`feature/*`** — Individual feature branches. Branch off from `develop`.
  - Naming: `feature/short-description` (e.g., `feature/add-contact-form`)
  - Delete after merge to `develop`

- **`release/*`** — Prepare for production release. Branch off from `develop`.
  - Naming: `release/v1.0.0` (e.g., `release/v1.2.0`)
  - Merge to both `main` (with tag) and back to `develop`
  - Delete after merge

- **`hotfix/*`** — Emergency fixes for production. Branch off from `main`.
  - Naming: `hotfix/short-description` (e.g., `hotfix/security-patch`)
  - Merge to both `main` and `develop`
  - Delete after merge

## Workflow Examples

### Starting a New Feature
```bash
git checkout develop
git pull origin develop
git checkout -b feature/my-feature
# Make changes and commit
git push -u origin feature/my-feature
# Create a Pull Request to develop
```

### Creating a Release
```bash
git checkout develop
git pull origin develop
git checkout -b release/v1.0.0
# Make any final adjustments (version bumps, etc)
git push -u origin release/v1.0.0
# Create PRs: one to main, one back to develop
# After merging to main, tag the release: git tag -a v1.0.0 -m "Release version 1.0.0"
```

### Emergency Hotfix
```bash
git checkout main
git pull origin main
git checkout -b hotfix/critical-bug
# Fix the bug and commit
git push -u origin hotfix/critical-bug
# Create PRs to both main and develop
```

## Pull Request Guidelines

- Write clear PR titles and descriptions
- Link to any related issues
- Wait for at least one review approval before merging
- Delete branch after merging
- Keep PRs focused on a single feature or fix

## Deployment

- **Merge to `develop`** → Automatically deploys to staging
- **Merge to `main`** → Manually deployed to production (via release process)
