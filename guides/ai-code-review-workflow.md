# AI code review workflow

AI can help write code quickly. That does not mean the same AI context should be the only reviewer.

The safest pattern is simple:

```text
Builder writes the change -> Reviewer critiques the diff -> Human/main agent decides -> Tests verify
```

This guide shows how to use AI as a second-pass reviewer without turning it into a rubber stamp.

## Why separate review matters

The agent that just wrote the code is biased toward finishing. It already has a story in its head about why the change works.

A separate review pass is useful because it starts with a different job:

- find what can break
- look for security mistakes
- check whether the diff matches the task
- identify missing tests
- flag unnecessary complexity

That does not make the reviewer automatically right. It just gives you a better decision surface.

## The basic workflow

### 1. Define the task

Write the task in one or two sentences.

```text
Add email validation to the signup form and show a useful error when the email is invalid.
```

Avoid vague tasks like:

```text
Improve the signup flow.
```

Vague tasks create vague diffs, and vague diffs are hard to review.

### 2. Let the builder implement

The builder should make the smallest useful change and run relevant checks.

Builder instructions:

```text
Implement only the requested change. Do not refactor unrelated files. After editing, run the relevant checks and summarize changed files.
```

### 3. Review the diff, not the story

The reviewer should inspect the actual diff. Do not only review the builder’s summary.

Reviewer prompt:

```text
Review this diff for correctness, security, edge cases, and unnecessary complexity.

Do not rewrite the code yet.
Return:
- blockers
- risks
- missing tests/checks
- simpler alternative, if any
- final verdict: approve / request changes
```

### 4. Decide what to fix

Not every reviewer suggestion is a blocker.

Use this rule:

| Finding | Action |
|---|---|
| Security issue | Fix before merge |
| Broken logic | Fix before merge |
| Failed build/test | Fix before merge |
| Missing important test | Usually fix before merge |
| Naming/style preference | Consider, but do not churn |
| Bigger refactor idea | Save for later unless needed |

### 5. Verify after fixes

After fixes, rerun the relevant checks. If the fix is non-trivial, review the new diff too.

## What reviewers should check

### Scope

- Does the diff solve the requested problem?
- Did it change unrelated files?
- Did it introduce a new dependency?
- Did it rewrite working code without need?

### Correctness

- Does the happy path work?
- What happens with empty, invalid, duplicate, or missing data?
- Are async/loading/error states handled?
- Are types and validations consistent?

### Security

- Are secrets kept out of source code and logs?
- Are auth checks server-side where needed?
- Can users access another user’s data by changing an ID?
- Are inputs validated before database/API use?
- Did a convenience fix weaken permissions?

### Reliability

- Does the build pass?
- Do tests cover the changed behavior?
- Does failure produce a clear error?
- Are external calls handled with timeouts or error paths when appropriate?

### UX

- Does the user know what happened?
- Are mobile layouts still okay?
- Are loading and empty states reasonable?
- Are labels accessible enough?

## Copyable review prompt

```text
You are an independent code reviewer. Review the diff below.

Focus on:
1. correctness
2. security/privacy
3. missing edge cases
4. unnecessary complexity
5. tests/checks that should be run

Do not rewrite code unless asked. Return:

Verdict: approve / request changes
Blockers:
Risks:
Suggested fixes:
Checks to run:

Diff:
[PASTE DIFF]
```

## Copyable fix prompt

Use this after review finds real issues:

```text
Fix only the issues listed below. Do not refactor unrelated code. After editing, summarize what changed and run the relevant checks.

Issues to fix:
[PASTE REVIEW FINDINGS]
```

## Common AI review failure modes

### Rubber-stamp review

Bad sign:

```text
Looks good! No issues found.
```

with no evidence.

Better review:

```text
I checked auth boundaries, changed files, form validation, and build impact. One risk: invalid email errors are shown visually but not announced to screen readers.
```

### Over-reviewing

A reviewer may suggest a full architecture rewrite for a small bug fix. Do not accept churn just because it sounds sophisticated.

### Reviewing the summary instead of the diff

The summary may omit the mistake. Always review the actual changed files or diff.

## Lightweight solo workflow

If you are working alone:

```bash
git diff
```

Then ask your AI tool:

```text
Review this diff as if it were a pull request. Find blockers only. Do not suggest style churn unless it affects maintainability or correctness.
```

## Done checklist

Before merging/shipping:

- [ ] Diff matches the task
- [ ] No unrelated files changed
- [ ] Security/auth/data risks reviewed
- [ ] Relevant checks pass
- [ ] Reviewer blockers resolved
- [ ] Remaining risks are documented
