# How to write Cursor rules

Cursor rules should tell the editor's AI how to behave inside one project.

## Start with project facts

```md
This is a Next.js 15 app using TypeScript, Tailwind, and Supabase. Use pnpm. Content lives in `content/`.
```

## Add commands

```md
Before reporting success, run:
- `pnpm typecheck`
- `pnpm lint`
- `pnpm build`
```

## Add boundaries

```md
Do not edit `.env`, generated files, or database migrations unless specifically asked.
```

## Add stack-specific preferences

Examples:

```md
Prefer server components unless interactivity is needed.
Use existing UI components before creating new ones.
Keep Supabase service-role logic server-side only.
```

## Avoid vague rules

Bad:

```md
Make it scalable and beautiful.
```

Better:

```md
Do not add global state unless data is shared across at least three routes.
```
