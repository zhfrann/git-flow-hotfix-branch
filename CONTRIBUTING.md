# Contributing to MyApp

Thank you for considering contributing to MyApp! Please follow these guidelines to keep the codebase clean and the workflow smooth.

## Table of Contents

1. [Code of Conduct](#code-of-conduct)
2. [Getting Started](#getting-started)
3. [Branching Strategy](#branching-strategy)
4. [Commit Message Convention](#commit-message-convention)
5. [Pull Request Process](#pull-request-process)
6. [Reporting Bugs](#reporting-bugs)

---

## Code of Conduct

Be respectful, inclusive, and constructive in all interactions. See the full policy in `CODE_OF_CONDUCT.md`.

---

## Getting Started

1. Fork this repository
2. Clone your fork: `git clone https://github.com/<your-username>/myapp.git`
3. Follow the [Installation Guide](docs/INSTALLATION.md) to set up your local environment
4. Create a branch for your work (see Branching Strategy below)

---

## Branching Strategy

We follow **Git Flow**:

| Branch type | Naming convention | Base branch | Merge into |
|---|---|---|---|
| Feature | `feature/<short-description>` | `develop` | `develop` |
| Bug fix | `bugfix/<short-description>` | `develop` | `develop` |
| Release | `release/<version>` | `develop` | `main` & `develop` |
| Hotfix | `hotfix/<short-description>` | `main` | `main` & `develop` |

**Hotfix branches** are reserved for critical bugs found in production. Always branch off `main` and merge back into both `main` and `develop`.

Example hotfix workflow:

```bash
# Create a hotfix branch from main
git checkout main
git pull origin main
git checkout -b hotfix/fix-token-expiry

# ... make your fix ...

git add .
git commit -m "fix: resolve token expiry not refreshing on long sessions"

# Merge into main
git checkout main
git merge --no-ff hotfix/fix-token-expiry
git tag -a v1.2.1 -m "Hotfix v1.2.1"

# Merge into develop to keep it up to date
git checkout develop
git merge --no-ff hotfix/fix-token-expiry

# Delete the hotfix branch
git branch -d hotfix/fix-token-expiry
```

---

## Commit Message Convention

We use [Conventional Commits](https://www.conventionalcommits.org/):

```
<type>(<scope>): <short description>
```

| Type | When to use |
|---|---|
| `feat` | A new feature |
| `fix` | A bug fix |
| `docs` | Documentation changes only |
| `style` | Formatting, missing semicolons, etc. |
| `refactor` | Code change that neither fixes a bug nor adds a feature |
| `test` | Adding or updating tests |
| `chore` | Build process, dependency updates |

Examples:

```
feat(tasks): add CSV export for task list
fix(auth): resolve token expiry not refreshing
docs(readme): update quick start section
hotfix(tasks): fix wrong record deleted on shared due date
```

---

## Pull Request Process

1. Ensure your branch is up to date with its base branch
2. Run all tests locally before opening a PR
3. Fill in the PR template completely
4. Request at least one reviewer
5. Address all review comments before merging
6. Delete your branch after merging

---

## Reporting Bugs

Please open a GitHub Issue and include:

- A clear title and description
- Steps to reproduce
- Expected vs. actual behaviour
- Screenshots if applicable
- Environment details (OS, browser, version)
