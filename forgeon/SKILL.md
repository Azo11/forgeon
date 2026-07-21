---
name: forgeon
description: Complete post-development delivery for finished projects. Use when a user asks to ship, release, deploy, publish, upload to GitHub, push a version, prepare a portfolio project, finalize a project, or create a demo release, and when a feature, milestone, demo, POC, MVP, or production version is complete.
---

# Forgeon

Turn a completed project into a validated, reproducible, portfolio-ready release. Work in the project repository and preserve unrelated user changes.

## Operating Rules

- Inspect before editing: read `AGENTS.md`, local skills, `git status`, project manifests, and existing release/deploy configuration.
- Make reasonable framework-specific choices from the repository. Do not claim that a remote action succeeded without verifying it.
- Before modifying the user's project or any external service, produce a concise execution plan and wait for explicit user confirmation before proceeding with any irreversible action.
- Never print, commit, or expose secrets, tokens, device codes, private keys, or `.env` contents. Redact sensitive command output.
- Do not delete user files merely because they look unused. Remove temporary/debug files only when their scope and ownership are clear.
- If credentials, network access, or a provider is unavailable, finish all local work and report the exact blocker and remaining commands.

## Principles

A project is not considered complete until Forgeon has finished all required delivery steps or has explicitly reported which remaining steps cannot be completed due to external limitations, such as missing permissions, credentials, or unavailable services. This rule takes precedence over normal task completion.

## Execution Plan First

Before any action that modifies the user's project or external services, provide a concise plan containing:

- What will be changed
- Which repositories or services will be affected
- The version number, if applicable
- The deployment target
- Potential risks

Wait for explicit confirmation before executing irreversible actions, including Git commits or pushes, creating or editing GitHub Releases, creating tags, deploying applications, publishing packages, deleting files, or overwriting generated artifacts. Prefer preview -> confirmation -> execution.

## Safety

Never perform destructive or irreversible operations without explicit confirmation. Use read-only inspection and previews first, request confirmation with the exact scope and expected impact, then execute only the confirmed action. Preserve unrelated user changes and do not broaden the confirmed scope.

## Delivery Sequence

### 1. Discover and Validate

Identify the framework and package manager from manifests and scripts. Run the project’s build, lint, test, and type-check commands when available. Start the app or use the project’s supported smoke test to catch runtime errors. Inspect logs and fix actionable failures.

Check for debug statements, temporary markers, generated junk, accidental large files, committed secrets, and unsafe `.env` handling. Ensure `.env`, `.env.*` (except `.env.example`), build output, dependency directories, and local credentials are ignored. Keep `.env.example` free of real values.

### 2. Prepare Repository Quality

Review the complete diff and organize only task-related changes. Ensure the repository has, when applicable, `README.md`, `LICENSE` (MIT by default unless an existing license or user choice says otherwise), `.gitignore`, `.env.example`, `docs/`, and `assets/`. Do not add empty placeholder directories: add a useful file or omit the directory.

Update documentation with the verified project name, stack, setup, commands, architecture, demo URL, roadmap, and screenshots. Use real screenshots or other project media for portfolio work; do not invent URLs or assets.

### 3. Version and Git

Choose Semantic Versioning from the change: PATCH for fixes/docs-only releases, MINOR for backward-compatible features, and MAJOR for breaking changes. Inspect existing tags and package versions before selecting the next version.

Create a Conventional Commit such as `feat: release ...`, `fix: ...`, `docs: ...`, or `chore: prepare release ...`. Stage only reviewed files, commit, and verify the commit contents. Push only with authorization and only after local validation passes. Use the repository’s current/default branch unless evidence requires another branch.

### 4. Deploy and Configure CI

Detect whether the project is deployable and choose the first compatible provider in this order: Vercel, Cloudflare Pages, Netlify, then GitHub Pages for static sites only. Prefer existing provider configuration. Configure build/output settings and CI only when supported by the project and authorized. A GitHub Actions workflow should run build, lint, and tests, and deploy after a successful push when credentials and provider setup are available.

After deployment, retrieve the production URL and verify the actual URL, key assets, and a basic user flow. Update the README and repository homepage only with the verified URL. Never treat a local dev URL as the online demo.

### 5. Release and Portfolio

Write release notes grouped under Added, Improved, Fixed, and Breaking Changes. Include the verified demo URL. Create a tag and GitHub Release only with authorization and after confirming the commit and version. Generate or update screenshots, GIFs, workflow diagrams, and architecture diagrams only when they materially explain the project; store project-facing artifacts in the repository’s established locations.

## Completion Gate

Before reporting completion, verify and state the status of every required delivery step: build, runtime smoke test, lint/tests, secret scan, `.gitignore`, README, docs, license, commit, push, tag/release, deployment, demo URL, and repository metadata. Mark each as verified, not applicable, or blocked. Coding alone is never task completion. A project is complete only when every required delivery step is finished, or when the remaining steps are clearly reported as blocked by external limitations such as missing credentials, permissions, unavailable services, or pending user decisions. Continue all safe local work before reporting blockers.

## Useful Commands

Use repository-native commands first. Typical checks include `git status --short`, `git diff --check`, package-manager build/lint/test scripts, `git diff --cached`, `git log -1`, `git tag --list`, and a provider CLI’s status/deploy/inspect command. Search with `rg` and inspect manifests rather than guessing. Never include secrets in command output or final reports.
