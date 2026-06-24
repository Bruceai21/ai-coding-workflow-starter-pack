# AI code review checklist

Use this before merging or publishing AI-assisted code.

## Scope

- [ ] Does the diff only change what the task requested?
- [ ] Are unrelated formatting/refactor changes avoided?
- [ ] Are generated files excluded unless intentionally updated?

## Correctness

- [ ] Does the happy path work?
- [ ] Are error states handled?
- [ ] Are empty/loading states handled?
- [ ] Are edge cases covered?
- [ ] Are types and validations correct?

## Security

- [ ] No secrets committed
- [ ] Server-only keys stay server-side
- [ ] Auth checks happen server-side where needed
- [ ] Users cannot access other users' data by changing IDs/URLs
- [ ] Inputs are validated before use

## Tests and build

- [ ] Typecheck passes
- [ ] Lint passes
- [ ] Unit/integration tests pass, if present
- [ ] Production build passes
- [ ] Manual smoke test completed, if needed

## UX

- [ ] Mobile layout still works
- [ ] Buttons/forms have useful labels
- [ ] Error messages are understandable
- [ ] No broken links or missing images

## Final question

Would you be comfortable explaining this change to another developer tomorrow?

If not, simplify or document it.
