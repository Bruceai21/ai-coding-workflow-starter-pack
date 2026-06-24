# Vibe coding launch audit

Before launching an AI-generated app, audit the boring parts.

## Audit areas

1. App purpose and user flows
2. Secrets and environment variables
3. Auth and authorization
4. Database/storage rules
5. Clean install and build
6. Mobile UX and error states
7. Monitoring, backups, and rollback

## Useful prompt

```text
Audit this app before launch. List every issue that could block production release, especially auth, secrets, database access, forms, deployment config, and rollback. Do not fix anything yet.
```

## Launch blocker examples

- API keys committed to GitHub
- admin checks only hidden in the UI
- public database reads that should be private
- production build fails
- payment webhook unverified
- no rollback path for important data

## Good outcome

The goal is not perfection. The goal is knowing what is safe, what is risky, and what you are intentionally deferring.
