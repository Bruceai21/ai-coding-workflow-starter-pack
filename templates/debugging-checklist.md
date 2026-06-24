# Debugging checklist

Use this when an AI coding session starts guessing.

## 1. Reproduce

- [ ] What exact command or user action fails?
- [ ] What is the full error message?
- [ ] Can the failure be reproduced twice?
- [ ] Did it work before? If yes, when?

## 2. Narrow the surface

- [ ] What files changed recently?
- [ ] What dependency/config changed recently?
- [ ] Is the failure local, CI-only, or production-only?
- [ ] Is it data-dependent?

## 3. Inspect before editing

- [ ] Read the failing file
- [ ] Read nearby tests
- [ ] Read related config
- [ ] Search for the same pattern elsewhere

## 4. Form one hypothesis

Write one sentence:

```text
I think this fails because [cause], and I can test that by [check].
```

## 5. Make the smallest fix

- [ ] Change one thing
- [ ] Re-run the failing check
- [ ] If it fails differently, update the hypothesis
- [ ] Do not stack random fixes

## 6. Verify

- [ ] Original failure is gone
- [ ] Related checks still pass
- [ ] The fix did not hide the error
- [ ] The final explanation is clear
