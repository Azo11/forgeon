Forgeon
项目完成后的发布、部署、上传 GitHub、版本交付和上线验证。
Forgeon is a post-development delivery skill for turning completed projects into validated, reproducible, portfolio-ready releases.

## Contents

- `forgeon/SKILL.md`: delivery workflow and safety rules
- `forgeon/agents/openai.yaml`: Codex UI metadata

## Installation

Copy the `forgeon/` directory into your Codex skills directory:

```sh
cp -R forgeon ~/.codex/skills/forgeon
```

Forgeon can then be invoked explicitly with `$forgeon` or triggered by release-oriented requests.

## Maintenance Workflow

Changes to Forgeon follow `AGENTS.md`: analyze the enhancement, explain impact and trade-offs, recommend an implementation, suggest a SemVer bump, present an execution plan, and wait for approval before editing or publishing.

Before a delivery workflow runs, Forgeon performs an Environment Check for Git, GitHub CLI, authentication, deployment access, required environment variables, and project framework detection. It reports each prerequisite as `verified`, `blocked`, or `not applicable` without exposing secret values.

Forgeon also uses Dry Run mode: it previews files, commands, external actions, and expected results, then waits for confirmation. Before irreversible actions it records the current commit, deployment state, and previous release reference. Failed deployments retain failure evidence and restore the previous version when supported and authorized.

## License

MIT
