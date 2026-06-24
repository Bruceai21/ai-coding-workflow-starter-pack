# Deployment checklist

Use before sharing an AI-generated or AI-assisted app publicly.

## Understand the app

- [ ] Plain-English app summary exists
- [ ] Main user flows are known
- [ ] Data collected by the app is listed
- [ ] External services are listed
- [ ] Failure points are known

## Secrets and environment

- [ ] `.env` is ignored by Git
- [ ] No API keys or tokens are committed
- [ ] Production secrets are set in the host dashboard
- [ ] Local/test keys are separate from production keys
- [ ] Browser code does not include server-only keys

## Auth and permissions

- [ ] Logged-out users cannot access protected pages
- [ ] Normal users cannot access admin pages
- [ ] User A cannot view/edit User B's data
- [ ] Direct API requests are checked server-side
- [ ] Database/storage rules match the app's privacy model

## Build and tests

- [ ] Clean install works
- [ ] Typecheck passes
- [ ] Lint passes
- [ ] Tests pass or missing tests are documented
- [ ] Production build passes

## Product smoke test

- [ ] Sign up / login / logout works
- [ ] Forms submit and validate correctly
- [ ] Emails/webhooks work if used
- [ ] Mobile layout works
- [ ] Error states do not expose sensitive details

## Operations

- [ ] Monitoring/logging exists or is intentionally deferred
- [ ] Backups exist for important data
- [ ] Rollback path is known
- [ ] Domain/DNS/SSL are working
- [ ] README has setup instructions

## Ship/no-ship rule

If auth, secrets, payments, or database permissions are unclear, do not ship yet.
