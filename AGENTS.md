# AGENTS.md

## Project Overview

This repository contains the Forgeon Codex skill, a post-development delivery workflow for preparing projects for release.

## Repository Structure

- `forgeon/SKILL.md`: Core skill instructions
- `forgeon/agents/openai.yaml`: Codex UI metadata
- `README.md`: Installation and project overview
- `LICENSE`: MIT license

## Change Rules

- Analyze each requested enhancement and explain its impact before editing.
- When multiple implementation options exist, explain the trade-offs and recommend one before making changes.
- Suggest a Semantic Versioning bump and show an execution plan before implementation.
- Wait for explicit user approval before making changes, committing, tagging, pushing, or creating a GitHub Release.
- Preserve the existing Forgeon workflow when making updates.
- Update the skill in place; do not create duplicate skill directories.
- Do not add secrets, tokens, credentials, `.env` files, or private URLs.
- Use `apply_patch` for manual edits.
- Keep documentation concise and use ASCII unless non-ASCII text is necessary.

## Validation

After changing the skill, run:

```sh
python3 /Users/shenmengyuan/.codex/skills/.system/skill-creator/scripts/quick_validate.py forgeon
```

Review the final diff and confirm that `forgeon/SKILL.md` and `forgeon/agents/openai.yaml` remain valid.

## Publishing

Publishing actions must follow Forgeon's execution-plan-first and preview-confirmation-execution rules. Never commit, tag, push, create releases, or overwrite generated artifacts without explicit confirmation. A project is not complete until every required delivery step is finished or remaining steps are clearly reported as blocked by external limitations.
