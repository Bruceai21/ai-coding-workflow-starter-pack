# How to use AGENTS.md

`AGENTS.md` is a project instruction file for AI coding agents. It tells the agent how your repo works before it starts editing files.

Think of it as a README for the agent instead of the user.

A normal `README.md` says:

- what the project does
- how humans install and use it
- where docs live

An `AGENTS.md` says:

- what commands verify a change
- what files should not be touched
- what architecture rules matter
- when the agent should stop and ask
- what “done” means in this repo

## Why it matters

AI coding tools are good at guessing. That is useful until the guess is wrong.

Without project instructions, an agent may:

- run the wrong package manager
- edit generated files
- skip the production build
- use a service-role key in browser code
- make broad refactors for a small request
- report success after only checking the happy path

A good `AGENTS.md` reduces those mistakes by making the boring facts explicit.

## Step 1: start with one root file

Put the file at the project root:

```text
my-project/
  AGENTS.md
  README.md
  package.json
  src/
```

Start with the template in this repo:

```bash
cp templates/AGENTS.md /path/to/your-project/AGENTS.md
```

Then replace every placeholder with project-specific details.

## Step 2: write a useful project purpose

Bad:

```md
This is my app.
```

Better:

```md
This is a Next.js booking site for a local cleaning business. The main goal is to capture quote requests and send them to the business owner by email.
```

That one sentence helps the agent make better choices about copy, forms, metadata, and risk.

## Step 3: add the commands that matter

Do not make the agent infer your workflow from `package.json` or old docs.

Example:

````md
## Commands

Run these from the repo root:

```bash
pnpm install
pnpm typecheck
pnpm lint
pnpm test
pnpm build
```

`pnpm test:e2e` is slow. Run it only for auth, checkout, routing, or critical user-flow changes.
````

If there are no tests, say so:

```md
There is no automated test suite yet. For UI changes, run `pnpm build` and manually check the changed page in the browser.
```

## Step 4: add a file map

Agents waste time and make bad edits when they have no map.

Example:

```md
## File map

- `src/app/` - Next.js routes
- `src/components/` - shared UI
- `content/blog/` - article markdown
- `public/images/` - static assets
- `scripts/` - maintenance scripts
```

Do not document every file. Document the folders where agents are likely to work.

## Step 5: define safety boundaries

This is where `AGENTS.md` earns its keep.

Example:

```md
## Safety boundaries

Ask before:

- deleting files
- editing `.env` values
- changing production deployment settings
- modifying authentication, payments, or database permissions
- running destructive migrations
- force-pushing or rewriting git history

Never print secrets, tokens, private keys, customer data, or webhook URLs.
```

If the project touches real users, money, private data, or infrastructure, make the boundary obvious.

## Step 6: define “done”

A task is not done when the code looks plausible. It is done when it has been checked.

Example:

```md
## Definition of done

Before reporting success:

1. Implement the requested change.
2. Run relevant checks.
3. Summarize changed files.
4. Report any failed checks honestly.
5. List follow-ups or risks.
```

This prevents the classic AI move: “I updated it” with no build, no tests, and no verification.

## When to add nested AGENTS.md files

Nested files help when one repo contains different apps or rules.

Good use:

```text
AGENTS.md
apps/web/AGENTS.md
apps/api/AGENTS.md
packages/ui/AGENTS.md
```

Root file:

```md
This monorepo uses pnpm workspaces. Run commands from the repo root unless a nested AGENTS.md says otherwise.
```

Nested file:

```md
This folder is the API service. Do not use browser-only packages here. Run `pnpm --filter api test` for API changes.
```

Bad use: copying the same giant instructions into every folder. That creates stale prompt soup.

## Maintenance checklist

Update `AGENTS.md` when:

- package manager changes
- test/build commands change
- deployment target changes
- auth/database/payment rules change
- new generated folders appear
- the project becomes a monorepo

An outdated `AGENTS.md` is worse than no file because the agent will follow bad instructions confidently.

## Copyable mini template

````md
# AGENTS.md

## Project purpose

[One paragraph explaining what this project does and what matters most.]

## Stack

- [Framework]
- [Language]
- [Package manager]
- [Database/backend]
- [Hosting]

## Commands

```bash
[install command]
[typecheck command]
[lint command]
[test command]
[build command]
```

## File map

- `src/` - [purpose]
- `tests/` - [purpose]
- `scripts/` - [purpose]

## Safety boundaries

Ask before changing secrets, auth, payments, database permissions, production config, or deleting data.

## Done means

Run the relevant checks, summarize changes, and report failures honestly.
````
