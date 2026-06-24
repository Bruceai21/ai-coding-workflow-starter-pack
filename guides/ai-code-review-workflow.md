# AI code review workflow

Use AI to build faster, but do not let the same context that wrote the code be the only reviewer.

## Simple workflow

1. Builder agent implements the task.
2. Reviewer agent checks the diff.
3. Main agent/human decides what changes to keep.
4. Tests/build verify the result.

## Reviewer prompt

```text
Review this diff for correctness, security, edge cases, and unnecessary complexity. Do not rewrite the code yet. Return blockers, risks, and suggested fixes.
```

## What to ask the reviewer

- What can break?
- What is under-tested?
- Are secrets or auth boundaries affected?
- Did the change touch unrelated files?
- Is there a simpler solution?

## Rule

The reviewer does not automatically win. It contributes a second perspective. The coordinator still owns the final decision.
