# How to use AGENTS.md

`AGENTS.md` is a project instruction file for AI coding agents. It gives the agent the context it should not have to rediscover every session.

## Put it at the repo root

```text
my-project/
  AGENTS.md
  README.md
  package.json
```

## Keep it specific

Good instructions:

```md
Run `npm run typecheck`, `npm run lint`, and `npm run build` before reporting success.
```

Weak instructions:

```md
Write clean code.
```

## Include the boring facts

- project purpose
- tech stack
- file map
- commands
- testing expectations
- safety boundaries
- definition of done

## Add nested files only when needed

If a monorepo has separate apps, nested files can help:

```text
AGENTS.md
apps/web/AGENTS.md
apps/api/AGENTS.md
```

Do not duplicate the same huge file everywhere. Use nested files for what is different.

## Update it as the project changes

An outdated `AGENTS.md` is worse than no file. When commands, architecture, or deployment rules change, update the instructions too.
