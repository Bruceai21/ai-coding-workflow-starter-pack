# AI Coding Workflow Starter Pack

Practical templates and checklists for working with AI coding tools without turning your repo into a haunted vending machine.

This starter pack is from [VibeCodeSource](https://www.vibecodesource.com/). It is designed for builders using tools like Claude Code, Cursor, GitHub Copilot, Codex-style agents, and other AI-assisted development workflows.

## What is inside

```text
templates/
  AGENTS.md
  CLAUDE.md
  cursor-rules.md
  subagent-roles.md
  code-review-checklist.md
  deployment-checklist.md
  debugging-checklist.md

examples/
  nextjs-saas/AGENTS.md
  content-site/AGENTS.md
  python-automation/AGENTS.md
  home-lab-dashboard/AGENTS.md

guides/
  how-to-use-agents-md.md
  how-to-write-cursor-rules.md
  ai-code-review-workflow.md
  vibe-coding-launch-audit.md

checklists/
  before-you-ship.md
  security-basics.md
  production-readiness.md
```

## Quick start

1. Copy `templates/AGENTS.md` into the root of your project.
2. Replace every placeholder with real project details.
3. Add the verification commands your agent should actually run.
4. Copy any checklists that match your project.
5. Keep the file short, specific, and boring where boring prevents damage.

```bash
cp templates/AGENTS.md /path/to/your-project/AGENTS.md
```

## Recommended first setup

For most projects, start with these four files:

- `AGENTS.md` - project rules and verification commands for coding agents
- `cursor-rules.md` - editor-level AI behavior rules
- `code-review-checklist.md` - second-pass review before merging or publishing
- `deployment-checklist.md` - pre-launch checks before users see the app

## What this is not

This is not a magic prompt pack. It will not make bad architecture good, skip testing, or turn every AI-generated app into production software.

It gives your AI tools better guardrails:

- what the project is
- how to run it
- what not to touch
- how to verify changes
- when to stop and ask a human

## Related VibeCodeSource guides

- [How to Write an AGENTS.md File for AI Coding Tools](https://www.vibecodesource.com/blog/agents-md-template-ai-coding/)
- [The AI Coding Customization Stack](https://www.vibecodesource.com/blog/ai-coding-customization-stack/)
- [How to Use AI Coding Subagents Without Creating Agent Chaos](https://www.vibecodesource.com/blog/ai-coding-subagents/)
- [The Vibe Coding Deployment Checklist](https://www.vibecodesource.com/blog/vibe-coding-deployment-checklist/)

## License

MIT. Use it, fork it, adapt it, and make your agent read the instructions before it starts swinging a wrench.
