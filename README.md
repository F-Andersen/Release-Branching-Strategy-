# Release Branching Strategy

This document outlines the **Release Branching Strategy** for the project. It ensures a smooth development process by managing the lifecycle of code from initial development to production. The strategy uses Git flow principles to organize branches and commits.

---

## Branches Overview

### 1. `main` (or `master`)
- The **main** branch represents the stable, production-ready version of the code. All released code that is live or deployed will be in this branch.
- **Do not** push directly to `main`. Changes are integrated into `main` via the `release` or `hotfix` branches.

### 2. `develop`
- The **develop** branch is the integration branch for features. All new features and bug fixes are merged into `develop` first.
- **Do not** push directly to `develop` unless it's a minor bug fix that doesn't require a separate feature branch.

### 3. `feature/{feature-name}`
- **Feature branches** are used to develop new features for the upcoming release.
- These branches should be branched off from `develop` and should focus solely on one specific feature.
- **Naming convention**: `feature/{feature-name}` (e.g., `feature/login-page`).
- When a feature is complete, it is merged back into `develop`.

### 4. `release/{release-version}`
- A **release** branch is used for final preparations before a release.
- It is created from `develop` and used for testing, bug fixing, and minor tweaks.
- **Naming convention**: `release/{version}` (e.g., `release/1.0`).
- After all the release preparation is complete, the branch is merged into both `main` and `develop`.

### 5. `hotfix/{hotfix-name}`
- A **hotfix** branch is used to quickly patch issues in production.
- It is created from `main` and merged back into both `main` and `develop` (or the current release branch).
- **Naming convention**: `hotfix/{bug-description}` (e.g., `hotfix/fix-login-error`).
- After the hotfix is deployed, the branch is deleted.

---

## Workflow

### Creating a New Feature
1. Create a feature branch from `develop`:
   ```bash
   git checkout develop
   git checkout -b feature/{feature-name}
"

/