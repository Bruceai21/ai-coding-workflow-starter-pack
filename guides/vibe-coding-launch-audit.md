# Vibe coding launch audit

Vibe coding can get an app from idea to demo fast. Launching is different.

Before you put an AI-generated or AI-assisted app in front of real users, audit the boring parts: secrets, auth, database rules, builds, forms, monitoring, backups, and rollback.

The goal is not perfection. The goal is knowing what is safe, what is risky, and what you are intentionally deferring.

## When to use this audit

Use it before:

- sharing a public app link
- collecting real user data
- enabling payments
- publishing a client project
- connecting production databases
- running paid traffic to a new app
- showing an app as portfolio proof

If the app only runs locally with fake data, keep building. If strangers or clients can touch it, audit it.

## 1. Know what you built

Write a short launch note:

```text
App:
Users:
Core flows:
Data collected:
External services:
Failure risks:
```

Example:

```text
App: Appointment request form
Users: website visitors and business owner
Core flows: visitor submits request, owner receives email, request is saved
Data collected: name, email, phone, service type, message
External services: Supabase, Resend, Vercel
Failure risks: email fails, database rule exposes requests, spam submissions
```

If you cannot explain the app this clearly, the app is not ready for launch.

## 2. Check secrets and environment variables

Before launch:

- no API keys committed to Git
- `.env` files are ignored
- production secrets are set in the hosting provider
- local/test keys are separate from production keys
- server-only keys are not used in browser code
- old test keys are removed if no longer needed

Useful search:

```bash
grep -RIn --exclude-dir=node_modules --exclude-dir=.git --exclude-dir=dist --exclude-dir=.next "sk-\|api_key\|secret\|password\|SUPABASE_SERVICE" .
```

Do not blindly trust search results. Inspect anything suspicious.

If you use GitHub, also pay attention to secret scanning alerts. If you use `rg`/ripgrep, adapt the search command to your environment. The point is not the exact command; the point is to look for accidental secrets before the internet does.

## 3. Test authentication and authorization

If the app has users, admin pages, uploads, payments, or private data, test the ugly paths.

Check:

- logged-out user visits protected page
- normal user visits admin page
- user A tries to view user B’s data
- expired session submits a form
- direct API request bypasses the UI

Try changing IDs in URLs:

```text
/dashboard/projects/123
/dashboard/projects/124
```

If you can see data you should not see, that is a launch blocker.

## 4. Review database and storage rules

AI-generated apps often look polished while database rules are wide open.

Check:

- which tables/collections exist
- who can read each one
- who can write each one
- whether users are scoped to their own rows
- whether admin-only data is protected server-side
- whether public data is intentionally public
- upload bucket permissions

Useful prompt:

```text
Review this app's database and storage access. List every table, collection, or bucket; who can read it; who can write it; and what could go wrong if a user sends direct API requests.
```

Then verify the answer in the actual database settings.

## 5. Run a clean install

Your app may work locally because of files or settings you forgot existed.

Test from a clean clone or clean folder:

```bash
git clone <repo-url> clean-test
cd clean-test
npm install
npm run build
npm test
npm run dev
```

Adapt the commands for your stack. The point is to prove the repo can run from its own instructions.

## 6. Build for production

A dev server can hide production problems.

Run the production build:

```bash
npm run build
```

Common failures:

- missing environment variables
- server/client boundary mistakes
- TypeScript errors
- broken imports
- unsupported browser/server APIs
- pages that cannot be statically generated

If the production build fails, do not launch.

## 7. Test boring user flows

Test the flows real users will hit:

- sign up
- log in
- log out
- password reset
- form submission
- invalid input
- duplicate submission
- empty states
- loading states
- error states
- mobile layout
- payment cancel/success if payments exist
- email delivery if email exists

For every form, try blank fields, invalid fields, long text, duplicate clicks, and refresh after submit.

## 8. Add basic monitoring and rollback

For a small launch, this can be simple.

Minimum:

- you can see server/app errors
- important form submissions are not silently lost
- database has a backup/export path
- previous deployment can be restored
- you know who owns each external service account

If data matters, backup matters.

## Launch blocker examples

Do not launch until fixed:

- API keys committed to GitHub
- production build fails
- service-role key appears in frontend code
- admin check only hides buttons in the UI
- users can access other users’ data
- payment webhook is not verified
- database writes are public by accident
- no way to recover important data

## Copyable audit prompt

```text
Audit this app before launch.

Focus on:
- secrets and environment variables
- authentication and authorization
- database/storage permissions
- forms and user input
- production build/deployment
- monitoring, backups, and rollback

Do not fix anything yet. Return:
1. launch blockers
2. high-risk issues
3. medium-risk issues
4. checks to run
5. questions for the owner
```

## Final ship/no-ship rule

Ship when you can say:

```text
I know what this app does, what data it handles, how users are protected, how it builds, how it fails, and how I would recover.
```

If you cannot say that yet, it is not a failure. It is just not launch day.
