# AGENTS.md - Next.js SaaS example

## Project purpose

This is a Next.js SaaS app with accounts, dashboard pages, billing, and user-owned data.

## Stack

- Next.js
- TypeScript
- Tailwind CSS
- Supabase or similar backend
- Stripe or similar payments
- Vercel deployment

## Commands

```bash
pnpm install
pnpm typecheck
pnpm lint
pnpm test
pnpm build
```

## Safety rules

- Do not put service-role keys in client code.
- Do not change billing or webhook behavior without review.
- Check server-side authorization for all user-owned resources.
- Treat database policy changes as high risk.

## Done means

- Build passes
- Auth/payment/data changes are explained
- User A cannot access User B's data
- Environment variable changes are documented without values
