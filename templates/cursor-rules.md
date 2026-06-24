# Cursor rules template

Use this as a starting point for Cursor project rules. Adapt it to your stack.

## Project context

- This project is: [short description]
- Main goal: [shipping goal]
- Primary stack: [framework/language]
- Package manager: [npm/pnpm/bun/uv/etc.]

## General behavior

- Make the smallest useful change.
- Read nearby files before editing.
- Follow existing naming, folder, and component patterns.
- Do not introduce new libraries unless asked or clearly justified.
- Prefer boring, maintainable code over clever abstractions.

## Commands to run

```bash
[package-manager] typecheck
[package-manager] lint
[package-manager] test
[package-manager] build
```

## Do not edit

- `.env` or secret files
- generated output such as `dist/`, `.next/`, `build/`, `coverage/`
- lockfiles unless dependency changes require it
- migration files unless the task is specifically about database changes

## Ask first

Ask before changing:

- authentication or authorization
- payment flows
- production deployment settings
- database schema or permissions
- destructive scripts
- public API contracts

## Review checklist

Before saying a task is complete, check:

- Does the app still build?
- Did the change affect mobile/responsive layout?
- Are loading, empty, and error states handled?
- Are secrets kept server-side?
- Is the change scoped to the request?
