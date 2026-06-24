# Security basics for AI-coded apps

AI tools can move fast enough to accidentally ship dangerous defaults. Check these before launch.

## Secrets

- [ ] `.env` files are ignored
- [ ] API keys are not in frontend code
- [ ] Service role/admin keys are server-only
- [ ] Old test keys are removed
- [ ] Webhook URLs are not printed in public logs

## Authentication

- [ ] Protected pages require a real session
- [ ] Admin routes check admin status server-side
- [ ] Sessions expire safely
- [ ] Password reset flow does not leak user info

## Authorization

- [ ] User-specific data is scoped to the user
- [ ] IDs in URLs cannot be changed to access other data
- [ ] API routes check permissions independently from the UI
- [ ] Storage buckets/uploads have clear rules

## Input handling

- [ ] Forms validate required fields
- [ ] Server validates important fields again
- [ ] File uploads are limited by type/size
- [ ] Error messages do not expose stack traces or secrets

## Dependencies

- [ ] New packages are actually needed
- [ ] Lockfile is committed
- [ ] Known vulnerabilities are reviewed

## Rule

If the AI assistant says "this should be secure," ask it to point to the exact files/rules that enforce security.
