---
name: web-quality
description: Use when building, changing or reviewing a web application, HTTP API or networked service - routes, authentication, database access, forms, uploads, background jobs, scrapers - or when asked for a security, performance or reliability review of one. Not for scripts, embedded, FPGA or offline tools, where these budgets do not apply.
---

# Web quality

`.claude/rules/code-style.md` holds the general security floor. This skill adds the checks and budgets that only make sense for web applications and services. Structure scales with the job: a small service gets clear functions, tests and safe defaults, not layers.

Budgets below are defaults. A project's own targets win; say which you used.

## Security review

Map first: stack, entry points, trust boundaries, roles, sensitive data, and secrets by name only. Then check each item and give it exactly one status: passed, fixed, found not fixed, not applicable, not checked.

1. Authorization on the server for every route and object; deny by default; admin routes included.
2. Input validation on the server for every field, even when the client validates.
3. Parameterized queries only.
4. Output encoding; dynamic HTML passes through a sanitizer.
5. Secrets: none in the repo, client bundle, client-exposed environment variables, logs or URLs.
6. Sessions and tokens: not in web storage; cookies `HttpOnly`, `Secure`, `SameSite`.
7. Passwords: a slow hash (Argon2id, or bcrypt with cost 12 or more).
8. CORS limited to known origins.
9. Rate limits on authentication and expensive endpoints.
10. Uploads: type, size and storage location checked; never executed.
11. Webhooks: signature verified; duplicates ignored by event ID.
12. Outbound calls: timeouts; no user-controlled URLs without an allow-list.
13. Deserialization: never of untrusted data with unsafe formats.
14. Dependencies: lockfile committed; known-vulnerable packages reported.
15. Errors and logs: no stack traces to users; no personal data or secrets in logs.
16. TLS verification on; debug flags off.

Fix order: leaked secrets, authorization, injection, payment integrity, hardening. Rotate a leaked secret before purging history. Small, safe changes over rewrites; one finding per commit. Never weaken a control to make something work, and never conclude "secure".

## Reliability

- Configuration validated at startup; fail fast with a clear message.
- Errors caught at boundaries and logged with context; never swallowed.
- Retries only for idempotent operations, with backoff, jitter and a cap. One idempotency key per user intent.
- Database changes by expand and contract; migrations reversible.
- Pagination on every list endpoint; no N+1 queries.
- Never fake success for payments or irreversible actions.

## Performance budgets

Measure before claiming. Report the workload, the percentile and before/after values.

| Area | Default budget |
|---|---|
| Largest Contentful Paint | 2.5 s or less |
| Interaction to Next Paint | 200 ms or less |
| Cumulative Layout Shift | 0.1 or less |
| JavaScript, gzipped | under 200 kB |
| API p95 | under 200 ms; cached or indexed reads 50 ms |
| Main-thread task | no task over 50 ms |

- Images and embeds declare dimensions; the main image is in the HTML and not lazy-loaded; no render-blocking third-party scripts.
- Virtualize long lists.

## Scraping and automation

- Read robots.txt and the terms first. A 401, 403 or 429 means stop and report. Honest User-Agent; no CAPTCHA solving or stealth.
- Most structured source first: API, then embedded JSON, then HTML.
- Every wait has a ceiling. Checkpoint with a temporary file and rename.
- End with a run summary: attempted, succeeded, failed, empty, not checked.
