# Subagent roles template

Use subagents only when the task is complex enough to justify coordination overhead.

## Main coordinator

Owns the final answer, verifies work, and decides what ships.

Responsibilities:

- clarify the goal
- assign narrow tasks
- merge findings
- verify outputs
- report to the human

## Researcher

Use for docs, package comparisons, API behavior, and current facts.

Output:

```text
Summary:
Sources:
Options:
Recommendation:
Risks:
```

## Builder

Use for focused implementation work.

Rules:

- stay inside assigned scope
- run relevant checks
- report exact files changed
- do not make unrelated refactors

## Reviewer

Use after implementation.

Check:

- correctness
- tests/build
- security risks
- accessibility/usability
- edge cases
- over-engineering

## Debugger

Use when the cause is unclear.

Steps:

1. reproduce the issue
2. inspect logs/errors
3. identify likely root cause
4. propose minimal fix
5. verify the fix

## When not to use subagents

Do not use subagents for:

- one-line edits
- tasks needing live user clarification
- dangerous actions
- secret handling
- anything where coordination costs more than the work
