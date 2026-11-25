# Workflow

## Plan

For a multi-step task, state a short plan where each step names its check:

```
1. <step> -> verify: <check>
2. <step> -> verify: <check>
```

Weak criteria ("make it work") mean a question is missing; ask it.

## Scope

- Do what was asked. Offer extras; do not add them. No unrequested files or installs.
- When the route is ambiguous and cheap to reverse, take the cheaper path and say so in one line.
- When offering options: 2 to 4, recommended first, one line of trade-off each.
- An unattended run takes the recommended defaults, names them as assumptions, and ends with a list of the decisions it made.

## Tests

- A bug fix starts with a test or reproduction that fails, then passes.
- Watch a new test fail before trusting it. Expected values come from hand-checked literals, not from the code under test.
- Mock only at system boundaries.
- A test with no assertion, a run over zero tests, and an exit code hidden behind a pipe are false passes.
- After the change, run the project's own tests, lint, type check and build that apply.

## Debugging

- Get a deterministic reproduction first.
- List a few hypotheses and change one variable at a time.
- After three failed fixes, stop changing code: name the assumption you now doubt and ask one diagnostic question.
- Remove temporary logging before finishing. Never fix flakiness with a sleep.

## Measurements and research

- Every count states its denominator. Report what ran, what failed, what came back empty and what was not checked.
- Only sources you opened count. Prefer primary sources. Date version-sensitive claims. Cite the exact URL you read; never construct one.
- Separate observed, inferred and unknown.
- A 200 status is not success; missing fields stay null, never `""` or 0.

## Subagents

A brief contains: the goal, what is already ruled out, the files to read first, the files it owns, the rules it must keep (copied in), how to verify, and the shape of the answer. Check a subagent by its diff or evidence, not by its report. Give a reviewer the artifact, never your verdict.

## Review findings

Verdict first. Each finding has a severity (critical, required, nit) and `file:line`. Zero findings is a valid result. State what was not checked.

## Git

- Commit, push or open a PR only when asked. Branch first if on the default branch.
- Commit subject: imperative, stands alone, follows the repository's existing convention and language. The body says why. Never `fix`, `update`, `misc`, `wip` alone.
- One logical change per commit or PR. A bug-fix PR includes the reproduction; a PR states its merge risk.
- Never commit secrets or files that look like credentials.
