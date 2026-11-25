# Code style

Pragmatic, short, readable, maintainable. Match the file you are in before anything below.

## Comments

- A comment explains why: a constraint, a trade-off, a workaround for a specific bug, a non-obvious decision. One line, two when the second adds a new fact.
- Never: restating the next line or the signature, step narration (`Step 1`, `First`, `Finally`), section banners, end-of-block markers, empty labels (`Main logic`, `Helper`), emoji, change history (`changed this`, `added below`), `TODO`.
- Missing work is reported to the user, not parked in a comment.
- A constant you tuned gets a one-line why. A public API doc comment exists only when it adds a contract the signature does not show.
- Keep comments that carry real information: business rules, protocol details, security or concurrency notes, licences.
- Cleaning comments never touches code.

## Structure

- Flat and direct. Do not abstract logic that is used once; no factory, strategy or interface with a single implementation; no options nobody asked for. Abstract on the third real use.
- Guard clauses and early returns instead of nested if-else.
- Idiomatic modern syntax of the language (destructuring, optional chaining, comprehensions, array methods) over hand-written loops and temporaries.
- Parse and validate at the edge; pass typed values inward. Keep I/O separate from decisions where that is cheap.
- No circular dependencies. No commented-out code, `_unused` variables or compatibility shims nobody needs.

Size signals, for code you are writing now: nesting 3 or more levels, a function over about 50 lines, a file over about 300 lines of logic, the same 5 lines in several places, boolean flag parameters, names like `data`, `result`, `temp`. Treat a signal as a prompt to reconsider, not a rule. Never refactor existing code to satisfy one, and never split by line count alone; mention it instead.

## Naming and errors

- Natural, precise names that follow the community convention: `is_valid`, not `check_if_input_is_valid`.
- Catch only what you handle or convert. No blanket try/except that only prints. No empty catch. No handling for impossible cases.
- Errors surface at boundaries and fail closed. An option that needs another option fails loudly; conflicting settings raise.
- Test presence, not truthiness, when 0 or an empty string is a valid value.

## Change hygiene

- Check the dependency manifest before importing. No new dependency without a reason the existing stack cannot meet.
- Exported names, public APIs, file formats and schemas are contracts: change them additively, or ask first. Anything internal can change freely.
- Derive version strings and counts from one source.
- No elision in delivered code (`// ...`, `rest unchanged`). If output must stop, say "X of Y done; resume from Z".
- Ask before deleting code or files you did not write.

## Security floor

Applies whenever the code handles outside input, credentials or a network.

- Outside input (users, files, network, model output, fetched pages) is untrusted: validate it; use parameterized queries; never build SQL, shell or HTML from strings.
- Authorize on the server for every request; deny by default.
- Secrets stay in the environment or a secret manager: never in the repo, logs, CLI arguments or client code. Report a leaked secret by kind and location, never by value.
- Every outbound call has a timeout. Retries are bounded and only for idempotent operations.
- Verify a package exists and is the intended one before installing it. Never weaken TLS, CORS or auth to make something work.
- Never conclude that something "is secure"; state what was checked.

## Performance claims

A performance claim carries the workload and before/after numbers, never a bare percentage. A change that does not beat run-to-run noise is reverted.
