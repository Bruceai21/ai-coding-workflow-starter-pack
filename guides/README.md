# Guides

These guides explain how to use the templates in this starter pack.

## Recommended reading order

1. [How to use AGENTS.md](how-to-use-agents-md.md)
2. [How to write Cursor rules](how-to-write-cursor-rules.md)
3. [AI code review workflow](ai-code-review-workflow.md)
4. [Vibe coding launch audit](vibe-coding-launch-audit.md)

## Quick map

| Guide | Use when | Outcome |
|---|---|---|
| `how-to-use-agents-md.md` | You want one project instruction file that coding agents can follow. | A practical root `AGENTS.md` with commands, file map, safety boundaries, and done criteria. |
| `how-to-write-cursor-rules.md` | You use Cursor and want project-specific AI rules. | A short rule file that tells Cursor how to work in your repo without prompt sludge. |
| `ai-code-review-workflow.md` | You want AI to help review code without rubber-stamping itself. | A builder/reviewer workflow with copyable prompts and blocker criteria. |
| `vibe-coding-launch-audit.md` | You are about to deploy/share an AI-built app. | A launch/no-launch audit for secrets, auth, data, build, monitoring, and rollback. |

The goal is not to add process for its own sake. The goal is to prevent the boring mistakes: wrong commands, missing auth checks, leaked secrets, vague prompts, and “it worked once locally” launches.
