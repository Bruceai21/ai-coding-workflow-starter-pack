# How to write Cursor rules

Cursor rules give Cursor’s AI project-specific instructions. They work best when they are short, concrete, and tied to the actual repo.

Do not use rules to say “write good code.” Use them to tell Cursor what good means in this project.

## What belongs in Cursor rules

Good Cursor rules usually cover:

- project purpose
- stack and package manager
- important folders
- commands to run
- coding preferences
- files not to edit
- safety boundaries
- review expectations

## Where to put Cursor rules

Cursor's rule system can change over time, so check the current Cursor docs for the exact supported filenames and folders. The practical pattern is the same either way: keep project-specific rules in the repo, close to the code they describe.

Common approaches include:

- a project rules file in the repo
- a `.cursor/` rules folder when supported
- a short rule document copied into Cursor's project settings

Do not hide important project instructions only in your personal editor settings. If the rule affects how the project should be maintained, it should live in the repo so future contributors and AI sessions see the same guidance.

Good repo-local rule topics:

- package manager and commands
- important folders
- stack-specific preferences
- files Cursor should not edit
- safety boundaries for auth, data, payments, and deployment

Avoid putting secrets, private credentials, customer data, or personal notes in Cursor rules.

## Start with project facts

Bad:

```md
This is a modern web app. Use best practices.
```

Better:

```md
This is a Next.js 15 app using TypeScript, Tailwind, Supabase, and pnpm. Marketing pages live in `src/app/(marketing)`. Dashboard pages live in `src/app/dashboard`. Shared components live in `src/components`.
```

That tells Cursor where to look and what assumptions are safe.

## Add commands Cursor should care about

Example:

````md
Before reporting success, run the relevant checks:

```bash
pnpm typecheck
pnpm lint
pnpm build
```

Use `pnpm test` for changes to business logic, auth, forms, or API routes.
````

If a command is slow or requires services, say that:

```md
`pnpm test:e2e` requires the local dev server and seeded test database. Do not run it unless the task touches auth, routing, checkout, or onboarding.
```

## Add boundaries

Cursor is often used inside an editor, which makes it easy to accept changes quickly. Boundaries matter.

Example:

```md
Do not edit:

- `.env` or secret files
- generated folders: `.next/`, `dist/`, `build/`, `coverage/`
- database migrations unless the task is specifically about schema changes
- lockfiles unless dependency changes require it
```

## Add stack-specific rules

For a Next.js app:

```md
Prefer server components unless interactivity is required. Keep client components small. Do not access server-only env vars in client components.
```

For a Supabase app:

```md
Keep service-role logic server-side only. For data access changes, explain which table policies protect user data.
```

For a content site:

```md
Do not invent tool behavior, pricing, or current features. If a claim depends on current docs, verify it before writing.
```

For a Python automation:

```md
Use environment variables for settings. Scripts used by cron should print nothing when idle and clear errors when failing.
```

## Avoid vague rules

Weak:

```md
Make the UI beautiful and scalable.
```

Better:

```md
Use existing button, card, and layout components before creating new ones. Do not add a new UI library without approval.
```

Weak:

```md
Write secure code.
```

Better:

```md
Do not expose server-only keys to browser code. Protected API routes must verify the session server-side.
```

## Rule size: smaller is better

A good project rule file should usually fit on one screen or two. If it becomes a giant manual, Cursor may follow the wrong part or ignore the important parts.

Put detailed docs in normal project files. Use Cursor rules for the behavior you want repeated every session.

## Copyable starter

````md
# Cursor project rules

## Project context

This is [project type] for [audience/use case]. The main goal is [goal].

Stack:
- [framework]
- [language]
- [package manager]
- [backend/database]
- [hosting]

Important folders:
- `[folder]` - [purpose]
- `[folder]` - [purpose]

## How to work

- Make the smallest useful change.
- Read nearby files before editing.
- Follow existing patterns before inventing new ones.
- Do not add dependencies unless clearly justified.

## Commands

Run relevant checks before reporting success:

```bash
[typecheck]
[lint]
[test]
[build]
```

## Do not edit

- `.env` or secret files
- generated output folders
- migrations unless asked
- unrelated files

## Ask first

Ask before changing auth, payments, production config, database permissions, destructive scripts, or public API behavior.
````

## Maintenance checklist

Update Cursor rules when:

- the package manager changes
- important folders move
- build/test commands change
- auth/database/deployment rules change
- repeated AI mistakes reveal a missing rule

Do not add a rule for every one-time preference. Add rules for mistakes you want to prevent repeatedly.
