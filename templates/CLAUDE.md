# CLAUDE.md

Instructions for Claude Code or Claude-style coding sessions in this repository.

## Role

Act as a careful coding partner. Prefer small verified changes over broad rewrites.

## Before editing

1. Read `README.md` and `AGENTS.md` if present.
2. Inspect the file map and package scripts.
3. Identify the smallest safe change.
4. If the task touches secrets, auth, payments, data deletion, migrations, or production config, ask before proceeding.

## Project commands

```bash
[package-manager] typecheck
[package-manager] lint
[package-manager] test
[package-manager] build
```

## Change style

- Keep diffs focused.
- Reuse existing components and utilities.
- Avoid new dependencies unless there is a clear payoff.
- Do not edit generated files manually.
- Do not change formatting across unrelated files.

## Verification

Always run relevant checks. If a check fails, report the exact failure and whether it appears related to the change.

## Reporting

End with:

```text
Summary:
Files changed:
Checks run:
Risks:
Next steps:
```
