# Forgeon

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

## License

MIT
