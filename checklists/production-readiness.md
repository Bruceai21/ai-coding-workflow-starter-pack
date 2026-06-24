# Production readiness checklist

Use this before moving from demo to real users.

## Build

- [ ] Production build passes
- [ ] Typecheck/lint pass
- [ ] No debug-only code remains
- [ ] Source maps/logging choices are intentional

## Data

- [ ] Important data is backed up
- [ ] Restore path is known
- [ ] Database migrations are reviewed
- [ ] Seed/test data is removed from production

## Reliability

- [ ] App has basic monitoring/logging
- [ ] Errors are visible to maintainers
- [ ] Third-party service failures are handled
- [ ] Rate limits are considered for public forms/APIs

## UX

- [ ] Mobile layout is checked
- [ ] Empty states are useful
- [ ] Loading states are visible
- [ ] Errors tell users what to do next

## Rollback

- [ ] Previous deployment can be restored
- [ ] Environment variables are documented
- [ ] Domain/DNS changes are understood

## Documentation

- [ ] README explains setup
- [ ] Required env vars are listed without secret values
- [ ] Known limitations are documented
