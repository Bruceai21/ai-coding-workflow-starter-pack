# AGENTS.md

Project-level instructions for AI coding agents working in this repository.

## Project purpose

[Describe what this project does, who it is for, and what outcome matters most.]

Example:

```text
This is a Next.js marketing site for a local service business. The main goal is lead generation through service pages, blog posts, and quote-request forms.
```

## Tech stack

- [Framework / runtime]
- [Language]
- [Database / backend]
- [Hosting provider]
- [Package manager]

## File map

```text
src/                 source code
src/components/      reusable UI components
src/app/             routes/pages
content/             markdown/content files
public/              static assets
tests/               automated tests
scripts/             maintenance scripts
```

Update this map so the agent does not have to guess.

## Commands

Run these from the project root unless noted.

```bash
# install
[package-manager] install

# development
[package-manager] dev

# checks
[package-manager] typecheck
[package-manager] lint
[package-manager] test
[package-manager] build
```

If a command is slow, flaky, destructive, or requires secrets, say so here.

## Definition of done

A task is not done until:

- the requested change is implemented
- relevant checks pass or failures are explained
- changed files are summarized
- risks or follow-ups are listed
- no secrets or generated junk were committed

## Coding rules

- Prefer small, focused changes.
- Use existing patterns before adding new architecture.
- Do not add a dependency for one helper function.
- Keep generated files, build output, and vendor files out of manual edits.
- Preserve public API behavior unless the task explicitly changes it.
- If touching auth, payments, database rules, secrets, or deployment, slow down and explain the risk.

## Testing rules

Before reporting success, run the narrowest useful checks first. Then run the full build/test command when the change affects production behavior.

If tests do not exist, say that clearly and perform manual verification where possible.

## Safety boundaries

Ask before:

- deleting files or data
- changing production configuration
- rotating secrets or editing `.env` values
- modifying billing, auth, payments, or permissions
- running destructive migrations
- force-pushing or rewriting git history

Never print secrets, tokens, private keys, customer data, or webhook URLs in logs or summaries.

## Output format

When finished, report:

1. What changed
2. Files changed
3. Commands/checks run
4. Result
5. Risks/follow-ups
